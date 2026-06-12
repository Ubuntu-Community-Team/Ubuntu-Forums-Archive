---
title: "Installing windows after Ubuntu?"
date: 2005-06-29
forum: General Help
---

### Post by ante0 on 2005-06-29
Hello
As the title says, can i install windows after i've installed Ubuntu?
I know the windows installation would write over the MBR on the hdd. So my only choice would be to install it onto another hd? 
Or can i save the mbr info to a floppy and use it after i've intsalled windows? =)

---

### Post by arnieboy on 2005-06-29
ideally u shd install any linux OS **after** u have installed windows.. make sure u have enuf space and partitions allocated for the same purpose.

---

### Post by DancingSun on 2005-06-29
I think generally, it is **not** advisable to install Windows after installing Ubuntu.

Another user just did this and is having some troubles:
[http://ubuntuforums.org/showthread.php?t=45089](http://ubuntuforums.org/showthread.php?t=45089)

Windows likes to be on the 1st partition at the beginning of the drive, so unless you already left a free partition at the beginning of the drive when installing Ubuntu, chances are, installing Windows now will give you a lot of headache.

---

### Post by artinla on 2005-06-29
The easiest way is to install windows on a second hard drive and just select the drive you want each boot in the bios boot order.

However, it is possible to save your MBR with grub and put it back.   There are even some threads on this forum for modifying your grub menu.lst file to add windows to your grub menu even when it is located on another hard drive.  

I suggest the first option is the most effective and avoids a lot of headaches.

Art

---

### Post by ante0 on 2005-06-30
Thank u guys, i will try to install windows on another drive later then =)

---

### Post by mingus on 2005-06-30
Just to throw in another two cents . . .

Actually, dealing with the MBR and boot setup is fairly straightforward, once you know how grub works - this should not be a problem, and certainly should not drive your decision

And while Windows does require being on the first partition - that varies significantly between, say, W98 and XP.  With W98, you must put the whole OS on the same first partition.  With XP, all that is required is what MS calls the "system partition", which literally is ntldr, ntdetect.com, and boot.ini.  This is the equiv of grubs stage2 and menu.lst (grub's stage1 being the equiv of what W$ puts in the MBR).  The rest of XP can be be on another partition.

Several other options you have are:

Install XP on whichever partition you want on the drive.  Create an XP boot floppy with those 3 files, modifying boot.ini to point to where the rest of XP is.  Boot from the floppy and you will load XP.  Or, a bit more adventurous . . .

Assuming you have room on the drive, create another partition for Ubuntu and copy your current Ubuntu to it using cp -a.  That frees space for XP.  This is not difficult to do as long as you understand how your system is partitioned and mounted. 

You could also tar a copy of Ubuntu to removable media, create new partitions allowing for XP, and restore from the tar.  The HowTo on creating a backup with tar provides the instructions.

If you use a second drive and want to dual-boot, grub can be a bit tricky.  Just keep in mind that grub's drive #1 (hd0) is always the first drive in the BIOS boot sequence, not the first on the IDE chain.  So if you boot from the 2nd drive, you'll need to tell grub that (hd0) is hdb, and you'll need to use grub's "map" command in your menu.lst stanza for booting XP.  You can ofcourse alternatively keep switching boot drives in the BIOS, but after a while that's a pain.

---

