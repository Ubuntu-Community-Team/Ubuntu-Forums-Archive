---
title: "Inserting Windows CD has broken ubuntu"
date: 2007-06-03
forum: General Help
---

### Post by TimJBart on 2007-06-03
I have had my Ubuntu running perfectly for about 4 months, but today I decided to install Windows onto a 50 GB NTFS partition I have on my drive.

I booted windows setup, **but before I installed anything** I quit out and rebooted because I wanted to check something in Ubuntu.

To my dismay, my hard drive will now not boot.  GRUB does not load and it just hangs.  

I used ubuntu live CD to check the drive with GpartEd, and it isn't detecting my ext3 partitions!!!???  Instead it is detecting 300GB of unallocated space!  

Can anyone think why this is?  How do I mount my HD so I can recover the data from it?

---

### Post by phidia on 2007-06-03
If the live cd isn't seeing/showing your partitions that obviously is not good.
You could try some type of recovery software, but that always seems hit or miss IMO.

Have you tried the "Recover broken system" option from the live cd boot menu? That may not work but it's worth a shot.

If you don't have any other options (this is why having a good back up is a very good idea) then you might try to re-install ubuntu but instead of selecting format the partition you would choose _not_ to format the install partiton. To be clear-I mean selecting the very same parameters and partition the orginal install was on-with the one execption e.g you don't format .  I don't know if that will work though. I have done that myself and I think it worked once out of half a dozen times of trying it.

---

### Post by TimJBart on 2007-06-03
OK thanks, that was along the lines of what I was thinking.

Where is the recover broken system option?  I have never seen that before

---

### Post by WalrusRU on 2007-06-03
Try SuperGRUB
[http://supergrub.forjamari.linex.org/?section=home](http://supergrub.forjamari.linex.org/?section=home)

---

### Post by Hendrixski on 2007-06-03
> **TimJBart said:**
> GRUB does not load and it just hangs.  

I used ubuntu live CD to check the drive with GpartEd, and it isn't detecting my ext3 partitions!!!???  Instead it is detecting 300GB of unallocated space!  


Sounds to me like you partitioned your disk drive.  That means that the windows cd took the liberty of wiping your whole drive and turning it into a 300 gig space on which it was about to install.  I don't know that you would have a "broken system" to repair... you may not have any system.

My advice, is that if the windows CD was so generous that it did all of that wiping out for you, then you should at least give it the professional courtesy to throw it in the trash can.  :-)  You'll be glad you did.

---

### Post by TimJBart on 2007-06-03
But I definitely didn't partition my hard drive.  It is as if the setup deleted the partition record without telling me!

---

### Post by floke on 2007-06-03
First, DON'T PANIC! Sometimes GParted can't read the files and reports it as unallocated space. This happened to me after installing PCLOS and allowing the Drakinstaller to format some partitions. Boot into a LiveCD and try typing 'sudo fdisk -l' into a terminal. This will tell you what partitions are on your system. From there, once we know which partition ubuntu is on we just need to fix grub. For that you can try this [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Or post back here are we can walk you through it.

---

### Post by pseudonym on 2007-06-03
> **TimJBart said:**
> But I definitely didn't partition my hard drive.  It is as if the setup deleted the partition record without telling me! What screen were you in exactly when you exited the Windows installation?

Oh, and btw, I don't think the trashcan is the best option. Your (legal) Windows CD should fetch you at least a few bucks (or quid in your case) on ebay. :)

---

### Post by phidia on 2007-06-03
The "Rescue broken system" option is available at the boot menu of the live or install cd. If the partition is there that option will also provide you a way to re-install grub. So the simpliest way is best. If that doesn't work you can try more difficult things.

---

