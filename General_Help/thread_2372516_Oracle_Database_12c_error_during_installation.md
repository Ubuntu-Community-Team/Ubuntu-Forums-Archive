---
title: "Oracle Database 12c error during installation"
date: 2017-09-26
forum: General Help
---

### Post by jmoreno97 on 2017-09-26
I had this error during the installation of Oracle Database 12c:

INFORMACIÓN: 
ext.unlikely+0x4bed): referencia a `naecta' sin definir
/u01/app/oracle/product/12/dbhome_1/lib//libn12.a(naeu.o): En la función `naeueai_delt':
naeu.c:(text.unlikely+0x4fc6): referencia a `naeetau' sin definir
/u01/app/oracle/product/12/dbhome_1/lib//libn12.a(naeu.o): En la función `naeucak_delt':
naeu.c:(text.unlikely+0x5026): referencia a `naecta' sin definir

INFORMACIÓN: 
collect2: error: ld returned 1 exit status

INFORMACIÓN: 
/u01/app/oracle/product/12/dbhome_1/plsql/lib/ins_plsql.mk:34: fallo en las instrucciones para el objetivo 'wrap'

INFORMACIÓN: 
make: *** [wrap] Error 1

---

