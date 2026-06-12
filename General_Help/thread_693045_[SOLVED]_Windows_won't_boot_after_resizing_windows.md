---
title: "[SOLVED] Windows won't boot after resizing windows partition"
date: 2008-02-10
forum: General Help
---

### Post by Super TWiT on 2008-02-10
I resized my windows partition using Gparted.  Everything went fine, and I can access all of my data from Ubuntu.  However, when I try to boot windows it says Grub Error 13: "Invalid or unsupported executable format".  I tried to change what partition to boot, as it said it couldn't boot the selected partition.  Now it gives me this error.  I have the windows partition set with a boot flag.  Here's my menu.1st entry for windows:```
title		Microsoft Windows XP Professional
root    	(hd0,3)
savedefault
makeactive
chainloader	+1
```

---

### Post by seventhc on 2008-02-10
Were you making the windows partition smaller? If so, you should have done a defrag first. I'm not sure if that should change the boot options, it is possible that some files didn't get moved correctly.
Someone else here might have a better idea though.

---

### Post by mrsteveman1 on 2008-02-10
You should first boot into the recovery console on an XP installation disk and run fixboot to repair the partition bootloader (not the mbr). Sometimes resizing tools can screw with the windows bootloaders a bit.

You may have to fsck the filesystem from another windows box or installation as well.

---

### Post by agim on 2008-02-10
Simple question, but its always good to check these things. Are you sure that Windows sits on hd0,3. Might be good to check it.

---

### Post by Super TWiT on 2008-02-19
Sorry I haven't posted in so long.  This problem is bigger than I thought.   Anyway, after getting into the XP recovery console, typing in bootcfg /rebuild it sees my operating system and I say y to add it.  I entered in the load identifier, which is the name I think, and for options, I put in /fastdetect.  (I figured that out after much searching.)  It said operating system successfully added.  However, when I try to boot xp it now says error loading operating system.  My Xp partition has been copied from one partition and back on again.  The drive did have errors but I ran chkdsk on the drive.  I ran chkdsk again to be sure all errors were gone and they were.  All the fixes I have seen for that error are in the bios.  However, I don't think the bios is to blame.  I have ran fixmbr and fixboot.  However, I have not ran fixboot since the hard drives errors have been fixed so I will try that now.  Is there any kind of journaling or log file that is saved?  Or is there any way to enable that?  That is one of the areas were Linux again beats windows.  I would just reinstall, but I don't know my product key.  I know there are ways to get this, but those tools are used within windows.  Is there anyway I can get the product code from within Ubuntu?

---

### Post by mrsteveman1 on 2008-02-19
Unless you are using a retail copy of XP on custom hardware, the certificate sticker should be on the case somewhere with the product key.

Reinstalling is definitely your best option right now, if fixboot and fixmbr (or fdisk /mbr) didn't fix the XP boot process I'm not sure what would. Can you get it to boot at all, IE can you make grub chainload the XP partition? If grub can't chainload the XP partitions volume boot record, the XP bootloader is trashed.

---

### Post by Super TWiT on 2008-03-09
The computer is custom hardware.  I guess that's one of the down sides to building your own computer:(   Fortuenately, since I have access to other computers, I was able to build [UBCD]("http://www.ultimatebootcd.com/").  This software came with [Magic Jellybean Key Finder]("http://www.magicaljellybean.com/keyfinder.shtml") which allowed me to get my product key from my old install.  Once I got that I just reinstalled windows.  This is why copy protection is bad!  I also ended up reinstalling Ubuntu as I was having grub issues.  I am sure it could have been fixed, but it was faster to copy the home folder to another drive, and to reinstall Ubuntu.  Thank you all for your help!

---

