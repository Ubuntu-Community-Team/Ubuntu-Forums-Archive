---
title: "Oracle10gR2 installation fails: undefined ref to 'nnfyboot'"
date: 2006-08-14
forum: General Help
---

### Post by aspa on 2006-08-14
I'm trying to install Oracle10gR2 on Ubuntu 6.06. The installation goes fine up to the linking phase where the installer reports 86% completion.

In linking phase i get the following error message dialog from OUI:

Error in invoking target 'utilities ctx_on' of makefile '/opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/rdbms/lib/ins_rdbms.mk'. See '/opt/oracle10g/u01/app/oraInventory/logs/installActions2006-08-12_11-54-03PM.log' for details.

The failing link command gives with the below error message:

% cd /opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/rdbms/lib
% make -f ins_rdbms.mk utilities ctx_on

...
- Linking tg4pwd utility
rm -f /opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/rdbms/lib/tg4pwd
gcc -o /opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/rdbms/lib/tg4pwd -L/opt/oracle10g
/u01/app/oracle/product/10.2.0/db_1/rdbms/lib/ -L/opt/oracle10g/u01/app/oracle/product/10.
2.0/db_1/lib/ -L/opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/lib/stubs/ -L/usr/lib -l
irc /opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/rdbms/lib/tg4pwd.o /opt/orac
le10g/u01/app/oracle/product/10.2.0/db_1/rdbms/lib/defopt.o /opt/oracle10g/u01/app/oracle
/product/10.2.0/db_1/rdbms/lib/homts.o -lagtsh -lpls10 -lplp10 -lclntsh -lsn
ls10 -lnls10 -lcore10 -lsnls10 -lnls10 -lcore10 -lsnls10 -lnls10 -lxml10 -lcore10 -lunls1
0 -lsnls10 -lnls10 -lcore10 -lnls10 /opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/lib/
libgeneric10.a `cat /opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/lib/sysliblist` -W
l,-rpath,/opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/lib -lm `cat /opt/oracle10g/
u01/app/oracle/product/10.2.0/db_1/lib/sysliblist` -ldl -lm -L/opt/oracle10g/u01/app/ora
cle/product/10.2.0/db_1/lib -lvsn10
/opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/lib//libagtsh.so: undefined reference to
`nnfyboot'
collect2: ld returned 1 exit status
make: *** [/opt/oracle10g/u01/app/oracle/product/10.2.0/db_1/rdbms/lib/tg4pwd] Error 1


Any ideas on how to fix this issue? Has anyone else managed to install 10gR2 on Ubuntu 6.06?

Which library contains the nnfyboot symbol?

---

### Post by aspa on 2006-08-22
i found the solution to this problem here

[http://forums.oracle.com/forums/thread.jspa?threadID=413032&tstart=0](http://forums.oracle.com/forums/thread.jspa?threadID=413032&tstart=0)

---

### Post by s_raghu20 on 2007-12-30
Helped ma as well, thanks a ton

---

