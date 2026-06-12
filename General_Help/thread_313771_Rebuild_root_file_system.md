---
title: "Rebuild root file system"
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
I am at a loss as how to recover from this problem as it appears to be related to an issue in the file system.

Help please,

Tom

---

### Post by taurus on 2006-12-06
Can you give the name of the two programs you edited when the system crashed?

---

### Post by mibikerguy on 2006-12-06
I was running a background process which polls the ttyS1 and writes data to a Round Robbin Data Base; running Misterhouse, a home automation program, and also editing two .pl files which I was developing. The Misterhouse was running in a seperate terminal and I was editing in a second terminal window. The background process was running "normally" and writing data approximately once every 10 minutes. The keyboard and mouse "locked up" and using the shift and arrow keys would not change terminal windows. The system did not respond to any of the "usual" things, i.e. ctrl+c; esc; repeated rapid HARD presses on the 'enter' key ;)!

Tom

---

