---
title: "Lexmark Laser printer driver error"
date: 2005-06-15
forum: General Help
---

### Post by xvlun on 2005-06-15
hi everybody,

i got the following problem: i just downloaded Lexmark Unix&Linux Printer Drivers for my s/w laserprinter from [here](http://www.downloaddelivery.com/srfilecache/print-drivers-linux-glibc2-x86.rpm.gz).

Aliening the rpm-Package and installing it using apt doesn't work because the path of their program seem to be hardcodet. So i installed  it manually in /usr/lexprint. As the program claimed to need libstdc++-libc6.1-1.so.2, i installed the package libstdc++2.9-glibc2.1 i got from rpmseek.com. After that i ran their .(setup.lexprint program which ended errorlessly. 

Now here is my problem. When trying to start /usr/lexprint/bin/lexprint a license agreement and a nice splash screen shows up telling me "Program error - Device listing failed - run setup.lexprint" (translated from the original german error message) and quits without any further clue. Even starting lexprint with -x (for debug) doesn't supply any information. 

regards jan

---

