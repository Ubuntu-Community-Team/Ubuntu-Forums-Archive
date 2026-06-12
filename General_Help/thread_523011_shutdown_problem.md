---
title: "shutdown problem"
date: 2007-08-11
forum: General Help
---

### Post by Johnny.P on 2007-08-11
My new installation of ubuntu doesn't seem to want to shutdown, it goes through all the motions but fails to turn off the machine. any help greatly appreciated.

---

### Post by tgalati4 on 2007-08-11
Look for errors in the files contained in /var/log.  

Sometimes you need to install updates after a new install to fix minor problems.  Linux in general doesn't work 100% after a fresh install--you need a little fine tuning.

---

### Post by burek on 2007-08-11
> **Johnny.P said:**
> My new installation of ubuntu doesn't seem to want to shutdown, it goes through all the motions but fails to turn off the machine. any help greatly appreciated.

apt-get install acpid 
maybe

or apm type, if you have old machine

---

### Post by Johnny.P on 2007-08-12
Thanks for the quick replies but I dont understand how to check for errors or ....apt-get install?
could you run it by me again a bit simpler?:)    many thanks

---

### Post by init1 on 2007-08-12
> **Johnny.P said:**
> Thanks for the quick replies but I dont understand how to check for errors or ....apt-get install?
could you run it by me again a bit simpler?:)    many thanks
You will need the terminal for these things. Accessories>System>Terminal (I think). Type into the terminal:
```

ls /var/log

```
That will show you the contents of the system log folder. 
```

cat /var/acpid

```
That will show you the events that occurred with power management. Cat shows you the contents of a file. 
```

sudo apt-get install programnamehere

```
Installs apps for you. Sudo gives you permission to do things you usually cannot. This is also typed into the terminal.

---

