---
title: "Changed device and partition names"
date: 2007-07-21
forum: General Help
---

### Post by osod88 on 2007-07-21
Hello,
I have a little problem with my Ubuntu 7.04. In my computer there are 2 hdd units, one of them is an scsi drive on a PCI card, the other one is an IDE drive. My problem is when I installed Ubuntu the installer gave the name 'sda' for the scsi drive and 'sdb' for the ide drive. I installed Ubuntu on the ide drive called sdb. When i'm trying to boot my system it can't start sometimes because the names are changed, the IDE is the 'sda' and the scsi is 'sdb'. In that case there are a 'couldn't access tty: job control turned off' error message. But it sometimes starts, without any modification in BIOS, or anything else. I use lilo bootloader. On the scsi drive is an other system.  So my question is: Is there any way to solve this problem without reinstalling the whole system?
Regards: osod88

---

### Post by ajgreeny on 2007-07-21
Which kernel are you running?  There was a difficulty, if I remember right, with the 2.6.20-15-generic, which has been sorted out with 2.6.20-16-generic.  Perhaps a kernel update will do the right thing for you.

---

### Post by osod88 on 2007-07-21
Hello,
The kernel version is 2.6.20-16
pityke@ubuntup4:~$ uname -a
Linux ubuntup4 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux
Since my last post I have find out when I leave a disk in the cd-rom drive and that's the first boot device, then my system starts well. (I use my motherboard's pop-up boot device selector to boot from the IDE device) When I installed my system that setting was actual, maybe that's the reason, why my device names are changing. But it's a little bit annoying to keep a disk always in the drive and pushing the F11 button to call the motherboard's boot device selector...
Thanks for your reply!
Regards: osod88

---

