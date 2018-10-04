# utl-benchmarks-and-functionality-EG-server-vs-workstation
Benchmarks and functionality EG server vs workstation. 

    Benchmarks and functionality EG server vs workstation

    github
    https://tinyurl.com/y84z9cog
    https://github.com/rogerjdeangelis/utl-benchmarks-and-functionality-EG-server-vs-workstation

    for details
    https://tinyurl.com/ybo54zp4
    https://github.com/rogerjdeangelis/utl-benchmarks-and-functionality-EG-server-vs-workstation/blob/master/sys_benccwyam2.docx

    *_____ ____                              _        _        _   _
    | ____/ ___| __   __ __      _____  _ __| | _____| |_ __ _| |_(_) ___  _ __
    |  _|| |  _  \ \ / / \ \ /\ / / _ \| '__| |/ / __| __/ _` | __| |/ _ \| '_ \
    | |__| |_| |  \ V /   \ V  V / (_) | |  |   <\__ \ || (_| | |_| | (_) | | | |
    |_____\____|   \_/     \_/\_/ \___/|_|  |_|\_\___/\__\__,_|\__|_|\___/|_| |_|

    ;

    This is somewhat dated.

      EG has its place but only in conjuction with a workstation

        1. Big data (single table > 1Tb)
        2. File server to workstation
        3. Big computation (64+ concurrent tasks lasting at least a week at average
           CPU utilization over 15% system wide)

    Benchmarks before and after CCW upgrades (not the latest upgrade - which may be worse)
    Before the latest upgrade I could run 32 simultaneous CCW jobs without the grid now
    I can only run 4 without the grid - CCW now have VM images)

    Benchmarks before and after EG Upgrade
    compared with same benchmarks on my 2008 Workstation
    all results in seconds seconds

    BENCHMARKS
                                                                         $600
                                                May 18       June 1      2008 Dell T7400
                                EG Before       EG After     EG After    Workstation

     SPDE(free with base sas)
     SDS not available in EG?
     SQL query (with SPDE index)      N/A*          N/A*         N/A*         0.45 ** best parallel index

     SASFILE(I have 64gb ram)
     SQL query (no index)             N/A**         N/A**        N/A**        4.30 ** no index!!


     Create data (22gb)               265           351          355           129
     Sort data                        305           333          331           181
     Index data (create)              227           152           51           111

     sql query (with index)          7.35          2.56         2.12          3.78
     sql query (without index)      32.34         27.13        10.74         10.59

     EG GRID
     Job (4 tasks)*                   231           98           99            114


     WORKSTATION GRID (no neeed to run)

     Workstation 8 simultaneous systasks (could run 32 on EG before upgrade - unix server had 32 cores)

     options noxwait noxsync;
     %let tym=%sysfunc(time());
     systask kill sys1 sys2 sys3 sys4  sys5 sys6 sys7 sys8;
     systask command "&_s -termstmt %nrstr(%query(1);) -log d:\log\a1.log" taskname=sys1;
     systask command "&_s -termstmt %nrstr(%query(2);) -log d:\log\a2.log" taskname=sys2;
     systask command "&_s -termstmt %nrstr(%query(3);) -log d:\log\a3.log" taskname=sys3;
     systask command "&_s -termstmt %nrstr(%query(4);) -log d:\log\a4.log" taskname=sys4;
     systask command "&_s -termstmt %nrstr(%query(5);) -log d:\log\a5.log" taskname=sys5;
     systask command "&_s -termstmt %nrstr(%query(6);) -log d:\log\a6.log" taskname=sys6;
     systask command "&_s -termstmt %nrstr(%query(7);) -log d:\log\a7.log" taskname=sys7;
     systask command "&_s -termstmt %nrstr(%query(0);) -log d:\log\a8.log" taskname=sys8;
     waitfor sys1 sys2 sys3 sys4  sys5 sys6 sys7 sys8;
     %put %sysevalf( %sysfunc(time()) - &tym);?

    * __                  _   _
     / _|_   _ _ __   ___| |_(_) ___  _ __  ___
    | |_| | | | '_ \ / __| __| |/ _ \| '_ \/ __|
    |  _| |_| | | | | (__| |_| | (_) | | | \__ \
    |_|  \__,_|_| |_|\___|\__|_|\___/|_| |_|___/

    ;
    EG FUNCTIONALITY VERSUS POWER WORKSTATION


    EG is an excellent platform for non-programmers but is anthema
    for programmers and program development.

    EG is useful for grid processing of big data(single table > 1TB)
    and big computation(64 cores with 10% cpu utilization for over 8hrs) and as a data
    server for power worstations.

    COMPARISON
    ===========

    Process flow and long complex batch runs are
    not the domain of SAS they are the domain of operating
    system or Perl scripts.

    Classic SAS on a Power workstation versus EG on a large server

    EG functionality versus Ppower workstation
    (I am biased)


                         *************
                     ****CLASSIC SAS  ****
                  ***    ===========      ***
                **   Command line  more ram  **

              **  Command macros  cores/user   **

             *         Notepad editors           *

            *    Xcmd       Proc R  Perl   IML/R  *

          **  sas code in clear text               **

          *  Proc python      Stop running program  *

         *    Task manager  Single click versioning  *

        ** Streaming log     ***    Fewer freezes     **

        * Command pipes   **     ** Multiple cursors   *

        * Less downtime ***        **    Function keys  *

        * No lockdown  **           ** No code loss Upg *

        * Window       **            *  Libname excel   *

        * %Window      *     EG       *More screen avail*

        * Magic String *     ==      *  Passthru excel   *

        * download/ftp  *           **                  *

        ** Email interfa **        ** No code wrapper  **

         *   Pmenu        **     ** No hidden mac vars *

          *Fse/fsv.fsbroese  *** editor prefix area   *

          ** Easy and freqent upgrade and hotfix   **

            * Fast column and table dictionaries  *

             * No lousy EG generated code(SQL)   *

              **  Programmable mouse           **

                ** Capture editor text      **

                  ***  Editor scripts     ***

                    ****             ****
                        *************


    *____      _    ____  ____  _____
    |  _ \    / \  / ___||  _ \|  ___|
    | |_) |  / _ \ \___ \| |_) | |_
    |  _ <  / ___ \ ___) |  __/|  _|
    |_| \_\/_/   \_\____/|_|   |_|

    ;


    Server and/or local power workstation

    How to detemine if a SAS local power workstation would benefit you
    as a SAS programmer over an EG server.

    The first question to ask is how often do you need to access a database schema where one
    or more tables are over 1TB. I define big data as computing problems where most
    of a users programming involves tables over 1TB. The other place for larger serves is
    massive simulations or parallelism over 64 concurrent jobs. Workstations are available
    with 64 cores.

    Should I use just the server or a sever plus workstation(or power laptop) for my SAS programming.
    Systems like Tableau, Oracle, Teradata, Midas and the IDR do not run well on a workstation.

    This is how IBM used to measure overall mainframe usability.

      1. Reliability - Do you get the answer you expect.
      2. Availability.
      3. Serviciability
      4. Performance
      5. Functionality
      6. Security

    I use either excel or SAS running on both platforms for comparisons.

      1. Reliability.
          There was a bug in SAS 9.3 where 'proc distinct' gave the wrong answer for very high
          carinality.
             Workstation: I downloaded the fix from SAS and installed it on my workstation in 30 minutes
             Server:      Reported it a couple of months ago and it is still not fixed

      2. Availability.
          Workstation: 99.9%
          Server:      75% (Mostly due to the fact that you need an internet connection and scheduled
          and non scheduled availability

      3. Serviceability:
          Workstation: I added a second esata III SSD to my laptop in 2 minutes
          Server: Generally mot possible

      4. Performance
          Workstation: Much more ram,RAID 0 SSD drives and 100% of the XEONs. Very fast response time
                       not like a server dial-up connection
          Server: Little Ram, SAN spinning raid 5 drives

      5. Functionality
          Workstation: You have an operating system, R, Python, Ghostscript, Perl, C, Java...
                       ODBC(excel access...), more disk space(Try getting 5TB ob the server)...
          Server:      Generally locked down most of the above not available.

      6.  Security
            Workstation: Only have a subset of data. Local and disk encryption.
            Server: Has the jewels so obviously a better targer for hackes.



