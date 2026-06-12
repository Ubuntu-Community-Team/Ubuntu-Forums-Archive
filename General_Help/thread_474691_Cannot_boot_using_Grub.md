---
title: "Cannot boot using Grub"
date: 2007-06-15
forum: General Help
---

### Post by idipous on 2007-06-15
Hi there. 

I have two hard drives, one having linux and another having windows. I have Ubuntu Feisty and everything was working ok up until I, for some reason, decided to unplug my hard drives (both of them) and replug them after a while. The outcome was that I can no longer boot either Linux or Windows. I get Error 15 and Error 17 (cannot mount partitions). The only solution I have found is typing e and then editing the /boot (hd1,0) to (hd0,0) pressing enter and then pressing b to boot.

The problem is that it does not seem to be saved and every time I want to boot Ubuntu I have to do this. For windows I am afraid I have to use a super Grub cd I have which although it claims to correct the problem actually I was not able to make it happen.

Is there any way to permentaly change this? I have tried using the live cdrom to reinstall Grub but I  have not been able to remount the partitions as stated to the forums.

Any help? Can I change Grub settings from within the Ubuntu OS?
thanks in advance
Andreas

---

### Post by confused57 on 2007-06-15
This thread explains how to edit your menu.lst & the Window's entry should boot your Window's drive:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Make sure to change the groot entry in your menu.lst:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

### Post by idipous on 2007-06-16
Thanks, with some reading everything came back to normal!
andreas

---

