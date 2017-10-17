# utl_max_value_across_rows_cols_simultaneously
Find the max value across all rows and columns and the max values column and row location

    ```  Max value not working (max value across all columns and rows)                                                                                                ```
    ```                                                                                                                                                               ```
    ```      Original subject   "Max value not working"                                                                                                               ```
    ```                                                                                                                                                               ```
    ```      I like out of the box questions!!!                                                                                                                       ```
    ```                                                                                                                                                               ```
    ```      Two solutuons.                                                                                                                                           ```
    ```      This problem is best solved using a matrix language?                                                                                                     ```
    ```                                                                                                                                                               ```
    ```      WORKING CODE (IML/R WPS/PROC-R)                                                                                                                          ```
    ```       R                                                                                                                                                       ```
    ```          max<-max(have)                                                                                                                                       ```
    ```          %put Max=&fromR;                                                                                                                                     ```
    ```                                                                                                                                                               ```
    ```       SAS                                                                                                                                                     ```
    ```          *proc tranpose cannot be used here;                                                                                                                  ```
    ```          %utl_gather(sd1.have,var,val,,lon,valformat=3.);                                                                                                     ```
    ```          select max(var) as max from lon                                                                                                                      ```
    ```                                                                                                                                                               ```
    ```  see                                                                                                                                                          ```
    ```  https://communities.sas.com/t5/SAS-Procedures/Max-values-not-working/m-p/404936                                                                              ```
    ```                                                                                                                                                               ```
    ```  see for Alea Iacta gather macro                                                                                                                              ```
    ```  https://github.com/clindocu/sas-macros-r-functions                                                                                                           ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```  HAVE                                                                                                                                                         ```
    ```                                                                                                                                                               ```
    ```     WORK.HAVE total obs=4                                                                                                                                     ```
    ```     ======================                       RULES                                                                                                        ```
    ```                                                                                                                                                               ```
    ```       AMT1    AMT2    AMT3    AMT4    AMT5                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```         2      57      39      61      70        Max is 98 at row 4 column 3                                                                                  ```
    ```        92      81      12      36      49                                                                                                                     ```
    ```        51      30      80       3      70                                                                                                                     ```
    ```        21      33      98      83      11                                                                                                                     ```
    ```                                                                                                                                                               ```
    ```  WANT                                                                                                                                                         ```
    ```  ====                                                                                                                                                         ```
    ```     R                                                                                                                                                         ```
    ```            row   col                                                                                                                                          ```
    ```       [1,]   4     3                                                                                                                                          ```
    ```                                                                                                                                                               ```
    ```       Max=98                                                                                                                                                  ```
    ```                                                                                                                                                               ```
    ```     SAS                                                                                                                                                       ```
    ```                                                                                                                                                               ```
    ```            max                                                                                                                                                ```
    ```       --------                                                                                                                                                ```
    ```             98                                                                                                                                                ```
    ```                                                                                                                                                               ```
    ```  *                _               _       _                                                                                                                   ```
    ```   _ __ ___   __ _| | _____     __| | __ _| |_ __ _                                                                                                            ```
    ```  | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |                                                                                                           ```
    ```  | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |                                                                                                           ```
    ```  |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|                                                                                                           ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  options validvarname=upcase;                                                                                                                                 ```
    ```  libname sd1 "d:/sd1";                                                                                                                                        ```
    ```  data sd1.have;                                                                                                                                               ```
    ```    array amts amt1-amt5;                                                                                                                                      ```
    ```    do rec=1 to 4;                                                                                                                                             ```
    ```      do idx=1 to 5;                                                                                                                                           ```
    ```        amts[idx]=int(100*uniform(5731));                                                                                                                      ```
    ```        keep amt:;                                                                                                                                             ```
    ```      end;                                                                                                                                                     ```
    ```      output;                                                                                                                                                  ```
    ```    end;                                                                                                                                                       ```
    ```  run;quit;                                                                                                                                                    ```
    ```                                                                                                                                                               ```
    ```  *____              _       _   _                                                                                                                             ```
    ```  |  _ \   ___  ___ | |_   _| |_(_) ___  _ __                                                                                                                  ```
    ```  | |_) | / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                                                 ```
    ```  |  _ <  \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                                                ```
    ```  |_| \_\ |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                                                ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```  %utl_submit_r64('                                                                                                                                            ```
    ```  source("C:/Program Files/R/R-3.3.2/etc/Rprofile.site", echo=T);                                                                                              ```
    ```  library(haven);                                                                                                                                              ```
    ```  have<-as.matrix(read_sas("d:/sd1/have.sas7bdat"));                                                                                                           ```
    ```  which(have == max(have), arr.ind = TRUE);                                                                                                                    ```
    ```  max<-as.character(max(have));                                                                                                                                ```
    ```  writeClipboard(max);                                                                                                                                         ```
    ```  ',returnVar=Y);                                                                                                                                              ```
    ```                                                                                                                                                               ```
    ```  %put Max=&fromR;                                                                                                                                             ```
    ```                                                                                                                                                               ```
    ```  *                           _       _   _                                                                                                                    ```
    ```   ___  __ _ ___    ___  ___ | |_   _| |_(_) ___  _ __                                                                                                         ```
    ```  / __|/ _` / __|  / __|/ _ \| | | | | __| |/ _ \| '_ \                                                                                                        ```
    ```  \__ \ (_| \__ \  \__ \ (_) | | |_| | |_| | (_) | | | |                                                                                                       ```
    ```  |___/\__,_|___/  |___/\___/|_|\__,_|\__|_|\___/|_| |_|                                                                                                       ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  * tranpose cannot be used here;                                                                                                                              ```
    ```  %utl_gather(sd1.have,var,val,,long,valformat=3.);                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  proc sql;                                                                                                                                                    ```
    ```    select max(val) as max from long                                                                                                                           ```
    ```  ;quit;                                                                                                                                                       ```
    ```                                                                                                                                                               ```
    ```  *                                                                                                                                                            ```
    ```   _ __ ___   __ _  ___ _ __ ___                                                                                                                               ```
    ```  | '_ ` _ \ / _` |/ __| '__/ _ \                                                                                                                              ```
    ```  | | | | | | (_| | (__| | | (_) |                                                                                                                             ```
    ```  |_| |_| |_|\__,_|\___|_|  \___/                                                                                                                              ```
    ```                                                                                                                                                               ```
    ```  ;                                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```  %macro utl_submit_r64(                                                                                                                                       ```
    ```        pgmx                                                                                                                                                   ```
    ```       ,returnVar=N           /* set to Y if you want a return SAS macro variable from python */                                                               ```
    ```       ,returnVarName=fromR  /* name for the macro variable from Python */                                                                                     ```
    ```       )/des="Semi colon separated set of R commands - drop down to R";                                                                                        ```
    ```    * write the program to a temporary file;                                                                                                                   ```
    ```    filename r_pgm "d:/txt/r_pgm.txt" lrecl=32766 recfm=v;                                                                                                     ```
    ```    data _null_;                                                                                                                                               ```
    ```      length pgm $32756;                                                                                                                                       ```
    ```      file r_pgm;                                                                                                                                              ```
    ```      pgm=&pgmx;                                                                                                                                               ```
    ```      put pgm;                                                                                                                                                 ```
    ```      putlog pgm;                                                                                                                                              ```
    ```    run;                                                                                                                                                       ```
    ```    %let __loc=%sysfunc(pathname(r_pgm));                                                                                                                      ```
    ```    * pipe file through R;                                                                                                                                     ```
    ```    filename rut pipe "c:\Progra~1\R\R-3.3.2\bin\x64\R.exe --vanilla --quiet --no-save < &__loc";                                                              ```
    ```    data _null_;                                                                                                                                               ```
    ```      file print;                                                                                                                                              ```
    ```      infile rut recfm=v lrecl=32756;                                                                                                                          ```
    ```      input;                                                                                                                                                   ```
    ```      put _infile_;                                                                                                                                            ```
    ```      putlog _infile_;                                                                                                                                         ```
    ```    run;                                                                                                                                                       ```
    ```    filename rut clear;                                                                                                                                        ```
    ```    filename r_pgm clear;                                                                                                                                      ```
    ```                                                                                                                                                               ```
    ```    * use the clipboard to create macro variable;                                                                                                              ```
    ```    %if %upcase(%substr(&returnVar.,1,1))=Y %then %do;                                                                                                         ```
    ```      filename clp clipbrd ;                                                                                                                                   ```
    ```      data _null_;                                                                                                                                             ```
    ```       length txt $200;                                                                                                                                        ```
    ```       infile clp;                                                                                                                                             ```
    ```       input;                                                                                                                                                  ```
    ```       putlog "*******  " _infile_;                                                                                                                            ```
    ```       call symputx("&returnVarName.",_infile_,"G");                                                                                                           ```
    ```      run;quit;                                                                                                                                                ```
    ```    %end;                                                                                                                                                      ```
    ```                                                                                                                                                               ```
    ```  %mend utl_submit_r64;                                                                                                                                        ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
G
