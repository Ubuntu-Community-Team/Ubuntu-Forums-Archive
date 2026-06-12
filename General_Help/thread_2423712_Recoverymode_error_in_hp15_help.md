---
title: "Recoverymode error in hp15 help"
date: 2019-07-27
forum: General Help
---

### Post by terereking17 on 2019-07-27
i am new in the forum :)


  I cant start ubuntu in my notebook hp15..  i had ubuntu for a while alongside windows 10 in this computer. I used  both OS normally until last week, when suddenly after choosing ubuntu in  grub it went to recovery mode, showing some errors like:

  " modsign: Couldn't get UEFI db list",
  "do_IRQ: 1.55 No irq habdler for vector",
  "do_IRQ: 2.55 No irq habdler for vector",
  ""do_IRQ: 3.55 No irq habdler for vector",
  "couldnt get size: 0x800000000000000e"


  and so on. I tried cfdisk and other commands, but it didnt work (or i did'nt write  the commands properly, perhaps?) It didn´t bother me much because i was already thinking about making a  new-clear install of both windows 10 and ubuntu this weekend(windows has  been a bit laggy lately), however.. I used a liveCD again today trying to recover my data before wiping my  hdd and making a clean install, but i forgot some of my files were  "protected"/"encrypted" so i wasn´t able to get all my docs,  classes,etc.


  Somehow now i cant even boot ubuntu, even in recovery mode. I  used a livecd again today in order to install repair-grub from the ppas,  but after making the socalled grub repair and rebooting my computer,  the problem stayed the same.

  here are some pictures and the test from the boot repair
  [https://imgur.com/gallery/8dLBXCm](https://imgur.com/gallery/8dLBXCm)
  [http://paste.ubuntu.com/p/BfNCWzV779/](http://paste.ubuntu.com/p/BfNCWzV779/)
  Thanks in advance!

---

### Post by terereking17 on 2019-07-29
This is what i've tried so far, with no results:

I installed and used via sudo and ppa the "grub-recovery" in the liveCD command prompt, but grub is still not available when turning on the computer (I checked the BIOS Menu and the secureboot/fastboot option is disabled; the same goes for the windows 10 fastboot).  
I can access to grub menu just through using "advanced boot options" in windows and choosing "Ubuntu".
Already in grub menu, I pressed "c" and changed "quiet splash" with "noapic noacpi nosplash". Still the same. Then I used "sudo blkid" in recovery mode, and looked whether the UUID in grub was the same as the one where my Ubuntu partition is(which is sda5, ext4 type). They were not different. What can I do? 

Here is another picture of the same problems listed in the first post, but just showing the errors as the recovery mode starts:

[http://imgur.com/a/34apLQJ](http://imgur.com/a/34apLQJ)



And here is my partition list: includes windows, ubuntu(ext4 and swap) and the win recovery partition(which came with computer by default;windows OEM and some programs,etc)

[http://imgur.com/a/CfPDGnz](http://imgur.com/a/CfPDGnz)

Thanks in advance!

---

