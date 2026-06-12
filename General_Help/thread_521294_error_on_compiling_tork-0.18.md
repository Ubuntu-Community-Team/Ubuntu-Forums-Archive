---
title: "error on compiling tork-0.18"
date: 2007-08-09
forum: General Help
---

### Post by CHNdonny on 2007-08-09
when i ./configure
it indicated :
./configure: line 36370: AX_FUNC_WHICH_GETHOSTBYNAME_R: command not found
wrong input (flag != 4) at admin/conf.change.pl line 117, <> line 1310.

and then make
showed:
kerrylabel.cpp:30:22: error: knewmenu.h: No such file or directory
make[3]: *** [kerrylabel.o] error 1
make[3]: Leaving directory `/home/donny/tork-0.18/src'
make[2]: *** [all-recursive] error 1
make[2]: Leaving directory `/home/donny/tork-0.18/src'
make[1]: *** [all-recursive] error1
make[1]: Leaving directory `/home/donny/tork-0.18'
make: *** [all] error 2
what happened to that?or do i need to install some relevant lib or -dev?
P.S.i use gnome and qt
dapper drake
thank you for help

---

