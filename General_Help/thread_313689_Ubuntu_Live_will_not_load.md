---
title: "Ubuntu Live will not load"
date: 2006-12-06
forum: General Help
---

### Post by mibikerguy on 2006-12-06
My ubuntu Live 6.06 which was totally operational has gone "belly up". I was running the gedit program in one window and another program in the other. Neither was writing to the HDD at the time. The OS locked up. Upon reboot, it would not do a complete load. Using ctrl-alt-F1, produces the following messages:

Uncompressing Linux ..... OK, booting the kernel
INIT: cannot execute /etc/init.d/rcS
INIT: entering run level: 2
INIT: cannot execute /etc/init.d/rc

after which it presents me with the following:

(none)Login:

It will not respond to my login name or anything else such as sudo;root;admin:

Using the GRUB rescue mode brings me to the same results as above.
I am at a loss as how to recover from this problem.

Help please,

Tom

---

### Post by wpshooter on 2006-12-06
Am I understanding your problem correctly ?

Are you running the O/S from the CD or have you installed it to and are running it from your hard drive ?

Thanks.

---

### Post by mibikerguy on 2006-12-06
I am running a single Ubuntu OS on a SATA drive. All has been working well until this afternoon. The error messages seem to indicate that there is a problem in the root file system. GRUB appears to be executing "normally", but the error messages come as the OS tries to load.
Is is possible to recover from a Ubuntu Live CD only those two files indicated by the error messages, or is there some other way to recover the root file system?

Tom

---

