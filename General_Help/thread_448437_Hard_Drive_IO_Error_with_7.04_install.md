---
title: "Hard Drive I/O Error with 7.04 install"
date: 2007-05-19
forum: General Help
---

### Post by archer007 on 2007-05-19
I get two "Hard Drive I/O Errors" when I try to install Ubuntu 7.04. In addition, GRUB and LILO will not install. I have tried 6.10 server and 7.04 desktop Ubuntu. Is my hard drive dead or is it something else? Help appreciated!

---

### Post by rocket777 on 2007-05-22
Could be you have a drive problem. If you got another machine and can dload and burn a cd, get this program:

[http://www.softpedia.com/get/System/Hard-Disk-Utils/MHDD.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/MHDD.shtml)

Set your system to boot this cd, and get familiar with the program. Hit f1 for help etc.

When you know your way around this program, (you should at minimum do a scan - f4) but you also want to check the smart registers using f8 I think - the command is "smart").

Then look for counters that sound like errors. Off hand, I recall there are often values like number of ecc errors, relocation sector count, etc. The values are different for different vendor drives, so it depends on your drive. 

This is the "memtest86" diag for hard drives. Handy utility.

---

