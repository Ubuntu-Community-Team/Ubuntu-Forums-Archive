---
title: "uninstalling"
date: 2007-05-06
forum: General Help
---

### Post by strivehosting on 2007-05-06
How do i uninstall ubuntu and when I do, does it get rid of the partition changes i made?

---

### Post by strivehosting on 2007-05-06
I need to uninstall Ubuntu off my laptop because I might just use it for my desktop. Can someone please tell me how to uninstall it so that it deletes the partitions and the changes to them I made.

Thanks you in advance! :)

---

### Post by Sef on 2007-05-06
Are you dual booting now, or going to put on another os?

---

### Post by strivehosting on 2007-05-06
I'm dual booting right now.

---

### Post by AdHavoc on 2007-05-06
Launch the Live CD and open GParted, then format the ext3 and swap partitions so they are the same as your first partition (probably NTFS or FAT32).  Then delete the partitions and resize the first partition to the maximum size so there is no unallocated space.

---

### Post by strivehosting on 2007-05-06
launch the live cd while running ubuntu or windows?

---

### Post by strabes on 2007-05-06
You boot from the live cd, so you wouldn't be running either.

---

### Post by strivehosting on 2007-05-06
nvm. Thanks guys.

---

### Post by strivehosting on 2007-05-06
so should i have 3 partitions after i do what you said? i have fat 16 - 70.57 mib, ntfs - 52.35 GIB, and fat 32 - 3.47 GIB. 
   Is that right?

---

### Post by strivehosting on 2007-05-06
err double post.

---

### Post by strivehosting on 2007-05-06
Okay. I did all that and now when i start up my computer it says GRUB Loading stage1.5. GRUB loading, please wait.....
Error 22

---

### Post by confused57 on 2007-05-07
You need to restore your Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by strivehosting on 2007-05-07
> **confused57 said:**
> You need to restore your Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Okay. which guide do I follow? And thank you very much for your help! :)

---

### Post by confused57 on 2007-05-07
> **strivehosting said:**
> Okay. which guide do I follow? And thank you very much for your help! :)

What I would do first is download & burn a copy of the Super Grub Disk(5-7 Mb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it is capable of restoring your Window's IPL code to your mbr, as well as boot Windows or Ubuntu

If you have a Window's install cd(not a recovery cd), see the Window's recovery console  method, which involves booting the Window's install cd, press "r" for recovery, then enter FIXMBR, to restore your mbr...this would be the easiest and fastest  if you don't want to download the Super Grub Disk.

If you have a floppy drive, you use the Win98SE oem boot floppy method as described in the link in my first reply...except you'd enter fdisk /mbr.

It's your choice, but make sure not to delete your Ubuntu partitions until you restore Window's IPL code to the mbr.

---

### Post by strivehosting on 2007-05-08
> **confused57 said:**
> What I would do first is download & burn a copy of the Super Grub Disk(5-7 Mb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it is capable of restoring your Window's IPL code to your mbr, as well as boot Windows or Ubuntu

If you have a Window's install cd(not a recovery cd), see the Window's recovery console  method, which involves booting the Window's install cd, press "r" for recovery, then enter FIXMBR, to restore your mbr...this would be the easiest and fastest  if you don't want to download the Super Grub Disk.

If you have a floppy drive, you use the Win98SE oem boot floppy method as described in the link in my first reply...except you'd enter fdisk /mbr.

It's your choice, but make sure not to delete your Ubuntu partitions until you restore Window's IPL code to the mbr.

Hmm, I already deleted the partitions. That is why im getting the error when I turn on my laptop saying:

GRUB Loading stage1.5.


GRUB loading, please wait ...
Error 22

and thats all that happens.

---

### Post by strivehosting on 2007-05-08
nvm. I'm pretty sure i figured it out. Thanks guys.

---

