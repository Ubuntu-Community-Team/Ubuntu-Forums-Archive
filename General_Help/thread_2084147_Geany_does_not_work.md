---
title: "Geany does not work"
date: 2012-11-14
forum: General Help
---

### Post by cqc on 2012-11-14
Hi! I have installed Geany to use it for C programing, but it does not work. I can compile project, but when i want to run it shows this message
```
./geany_run_script.sh: 5: ./geany_run_script.sh: ./nees: not found


------------------
(program exited with code: 127)
Press return to continue



```
I couldnt find any solution on google, so please anyone help me.
Thanks

---

### Post by curtlee2002 on 2013-03-31
Click "build" instead of "compile".  You are just making an object file "nees.o" instead of "nees".  So "nees" isn't there for geany to execute.

---

