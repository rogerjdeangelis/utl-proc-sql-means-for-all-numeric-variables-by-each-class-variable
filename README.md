# utl-proc-sql-means-for-all-numeric-variables-by-each-class-variable
Proc sql means for all numeric variables by each class variable_do over varlist 
    %let pgm=utl-proc-sql-means-for-all-numeric-variables-by-each-class-variable_do-over-varlist;                           
                                                                                                                            
    Proc sql means for all numeric variables by each class variable_do over varlist                                         
                                                                                                                            
    There are better ways to do this than SQL but I think the op wants to use SQL.                                          
                                                                                                                            
    github                                                                                                                  
    http://tinyurl.com/y4q2y9kj                                                                                             
    https://github.com/rogerjdeangelis/utl-proc-sql-means-for-all-numeric-variables-by-each-class-variable                  
                                                                                                                            
    SAS Forum                                                                                                               
    http://tinyurl.com/y6no2uhb                                                                                             
    https://communities.sas.com/t5/SAS-Procedures/How-to-do-loop-for-the-same-query-on-different-varibles/m-p/542891        
                                                                                                                            
                                                                                                                            
    macros                                                                                                                  
    https://tinyurl.com/y9nfugth                                                                                            
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                              
                                                                                                                            
                                                                                                                            
    *_                   _                                                                                                  
    (_)_ __  _ __  _   _| |_                                                                                                
    | | '_ \| '_ \| | | | __|                                                                                               
    | | | | | |_) | |_| | |_                                                                                                
    |_|_| |_| .__/ \__,_|\__|                                                                                               
            |_|                                                                                                             
    ;                                                                                                                       
                                                                                                                            
    SASHELP.SHOES and these macro variables                                                                                 
                                                                                                                            
      1. CLASSVARS="REGION","PRODUCT","SUBSIDIARY"                                                                          
                                                                                                                            
      2. VARSN=4                                                                                                            
         VARS1=STORES                                                                                                       
         VARS2=SALES                                                                                                        
         VARS3=INVENTORY                                                                                                    
         VARS4=RETURNS                                                                                                      
                                                                                                                            
    SASHELP.SHOES total obs=395                                                                                             
                                                                                                                            
     REGION  PRODUCT         SUBSIDIARY    STORES   SALES  INVENTORY  RETURNS                                               
                                                                                                                            
     Africa  Boot            Addis Ababa     12     29761    191821      769                                                
     Africa  Men's Casual    Addis Ababa      4     67242    118036     2284                                                
     Africa  Men's Dress     Addis Ababa      7     76793    136273     2433                                                
     Africa  Sandal          Addis Ababa     10     62819    204284     1861                                                
     Africa  Slipper         Addis Ababa     14     68641    279795     1771                                                
     Africa  Sport Shoe      Addis Ababa      4      1690     16634       79                                                
     Africa  Women's Casual  Addis Ababa      2     51541     98641      940                                                
     Africa  Women's Dress   Addis Ababa     12    108942    311017     3233                                                
                                                                                                                            
    ....                                                                                                                    
                                                                                                                            
    %array(vars,values=%utl_varlist(sashelp.shoes,keep=_numeric_));                                                         
                                                                                                                            
    %let classvars=%utl_varlist(sashelp.shoes,keep=_character_,Qstyle=double,od=%str(,));                                   
                                                                                                                            
    *            _               _                                                                                          
      ___  _   _| |_ _ __  _   _| |_                                                                                        
     / _ \| | | | __| '_ \| | | | __|                                                                                       
    | (_) | |_| | |_| |_) | |_| | |_                                                                                        
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                                       
                    |_|                                                                                                     
    ;                                                                                                                       
                                                                                                                            
     LOG total obs=3                                                                                                        
                                                                                                                            
      CLASSVAR      RC              STATUS                                                                                  
                                                                                                                            
      REGION         0    Table  REGION  created                                                                            
      PRODUCT        0    Table  PRODUCT  created                                                                           
      SUBSIDIARY     0    Table  SUBSIDIARY  created                                                                        
                                                                                                                            
                                                                                                                            
                                                                                                                            
    WORK.REGION total obs=10                                                                                                
                                     MEAN_       MEAN_        MEAN_       MEAN_                                             
       REGION                        STORES      SALES      INVENTORY    RETURNS                                            
                                                                                                                            
       Africa                        9.5000     41831.93    126804.88    1322.98                                            
       Asia                          4.6429     32873.64     84009.93     778.21                                            
       Canada                       11.9459    115019.24    354343.49    3497.14                                            
       Central America/Caribbean    16.8438    114304.78    317933.69    3965.56                                            
       Eastern Europe               12.2258     77256.13    256531.32    2796.81                                            
       Middle East                  16.5417    234657.46    592031.21    8620.00                                            
       Pacific                       7.9111     51039.87    177139.80    1713.98                                            
       South America                11.7037     45088.57    110853.59    1904.65                                            
       United States                15.4250    137599.65    414559.93    4687.55                                            
       Western Europe               10.3548     78596.77    239391.13    2737.98                                            
                                                                                                                            
     ...                                                                                                                    
                                                                                                                            
    WORk.PRODUCT total obs=8                                                                                                
                                                                                                                            
                                     MEAN_       MEAN_        MEAN_       MEAN_                                             
       PRODUCT                       STORES      SALES      INVENTORY    RETURNS                                            
                                                                                                                            
       Boot                         16.6154     45202.75    187012.90    1896.58                                            
       Men's Casual                  8.8667    176304.60    379672.29    6911.89                                            
       Men's Dress                   9.6000    110144.86    290146.80    3281.98                                            
       Sandal                       11.5102     17723.18     65964.80     778.98                                            
       Slipper                      15.2692    118766.04    427526.54    4037.31                                            
       Sport Shoe                   12.0784     12773.86     65151.02     493.71                                            
       Women's Casual                6.0000     91952.47    215481.13    2919.87                                            
       Women's Dress                12.0392    122087.75    378525.08    3797.12                                            
                                                                                                                            
    *          _       _   _                                                                                                
     ___  ___ | |_   _| |_(_) ___  _ __                                                                                     
    / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                    
    \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                   
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                   
                                                                                                                            
    ;                                                                                                                       
                                                                                                                            
    %symdel cc / nowarn;                                                                                                    
    data log;                                                                                                               
                                                                                                                            
      length classvar $32; * important;                                                                                     
                                                                                                                            
      do classvar=&classvars;                                                                                               
                                                                                                                            
         call symputx("classvar",classvar);                                                                                 
                                                                                                                            
         rc=dosubl('                                                                                                        
            proc sql;                                                                                                       
              create                                                                                                        
                table &classvar. as                                                                                         
              select                                                                                                        
                &classvar                                                                                                   
               ,%do_over(vars,phrase=%str(                                                                                  
                   mean(?) as Mean_? ), between=comma)                                                                      
              from                                                                                                          
                sashelp.shoes                                                                                               
              group                                                                                                         
                by &classvar.                                                                                               
            ;quit;                                                                                                          
            %let cc=&syserr;                                                                                                
         ');                                                                                                                
                                                                                                                            
         if symgetn("cc")=0 then status=catx("  ","Table",classvar,"created");                                              
         else status=catx("  ","table",classvar,"Failed");                                                                  
         output;                                                                                                            
                                                                                                                            
      end;                                                                                                                  
                                                                                                                            
    stop;                                                                                                                   
    run;quit;                                                                                                               
                                                                                                                            
