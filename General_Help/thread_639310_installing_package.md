---
title: "installing package"
date: 2007-12-13
forum: General Help
---

### Post by dr.eslami on 2007-12-13
How can I solve this problem?
reza@reza-desktop:~$ dselect
The program 'dselect' is currently not installed.  You can install it by typing:
sudo apt-get install dselect
bash: dselect: command not found
reza@reza-desktop:~$ sudo apt-get install dselect
[sudo] password for reza:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
reza@reza-desktop:~$ dpkg --configure -a
.dpkg: requested operation requires superuser privilege
 Thanks
 Reza

---

### Post by FuturePilot on 2007-12-13
Run the last command you did there but with ```
sudo
```in front of it.

```
sudo dpkg --configure -a
```

---

### Post by dr.eslami on 2007-12-13
Thanks a lot. The problem solved with your help.

---

