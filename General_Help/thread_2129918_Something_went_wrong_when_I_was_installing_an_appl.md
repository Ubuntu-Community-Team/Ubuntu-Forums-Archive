---
title: "Something went wrong when I was installing an application"
date: 2013-03-27
forum: General Help
---

### Post by thorbs on 2013-03-27
Something went wrong when I was installing an application (Geany)

Now I am told to run manually sudo dpkg --configure -a 


But when I do that I get

sudo: unable to open /var/lib/sudo/thorbjrn/1: Read-only file system
dpkg: error: unable to access dpkg status area: Read-only file system


Anybody who can make sense of this?

---

### Post by slickymaster on 2013-03-27
Sounds like your hard drive is remounted as read only. That's usually because the system has detected file system damage. Boot up with an Ubuntu live CD or live USB, make sure the disk is unmounted, and then run the **fsck** command in the terminal.
Another thing you can do is to run the **dmesg** command and the last few lines might give you information why the disk was remounted read-only.

---

