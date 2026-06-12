---
title: "Identify running processes"
date: 2012-11-26
forum: General Help
---

### Post by jefe9 on 2012-11-26
Hi all
 
I am running Ubuntu 12.04 on an HP laptop;
 
I suspect that there is a runaway process on the system;
 
How can I tell a process name, firstly from a command prompt ( preferably directing the list to a file )
and secondly is there a way to identify the process name from within a Java ( or C++ ) program?
 
Thanks in Advance
 
Jefe

---

### Post by Habitual on 2012-11-26
Terminal > 
```
man ps
```

EXAMPLES section should get you started.

---

### Post by QIII on 2012-11-26
If you think you have a runaway at the moment, post back the results of ```
top
```
or install htop```
sudo apt-get install htop
```
and post the results of ```
htop
```

---

