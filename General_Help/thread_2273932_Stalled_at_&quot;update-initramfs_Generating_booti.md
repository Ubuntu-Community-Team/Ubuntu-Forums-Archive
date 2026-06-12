---
title: "Stalled at &quot;update-initramfs: Generating /boot/initrd.img....&quot;"
date: 2015-04-16
forum: General Help
---

### Post by jon54 on 2015-04-16
I recently installed Lubuntu from the  lubuntu-14.04.1-alternate-i386.iso file, and everything went well.  Upon rebooting, I ran apt-get update, and everything behaved as normal. 

When I went to run "apt-get upgrade", it got all the files it needed, then stalled out at "update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic".  I left it alone for an hour but it didn't budge (the machine was otherwise useable, it's just that screen didn't get past that point).  

So I killed the stalled process and tried to run apt-get update again, where I am told "dpkg was interrupted, you must manually run "dkpg --configure -a" to correct the problem. 

So I run that command, and end up right back stalling out at the "update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic" line. 

I saw [this](http://ubuntuforums.org/showthread.php?t=1005049) thread, but it was of no help. 

Any ideas on this?

---

