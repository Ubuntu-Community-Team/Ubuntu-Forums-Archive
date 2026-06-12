---
title: "Windows file recovery for Linux formatted partition"
date: 2007-09-17
forum: General Help
---

### Post by micheldb10 on 2007-09-17
My 13 year old seems to have accidently partitioned his hard drive in 2 linux partitions. He had Win XP (NTFS), but installed Ubuntu on it.  Using GPART, it shows two ~76GB partitions in EXT3 format and two 2GB swap partitions......but no NTFS partitions.  He doesn't think that he installed it twice.  Ubuntu was working fine after installing it.  He said that he was in XP and was defragging when he got a Windows critical error, so he rebooted.  Now, the Boot Loader does not show XP as an option under other OS.  Ubuntu sees two linux partitions (with linux files on it).   I installed the dirive in any other computer.  Device Manager sees 2 partitions, but Win Explorer does not recognize the linux partitions.  Does anyone know how to retrieve data that was under Win XP after the being partitioned/formatted in Linux?  I have pictures that I would like to save.  Are there any disk recovery tools?  Any help would be appreciated.  Thanks in advance.
Michel

---

### Post by tgalati4 on 2007-09-17
It's unfortunate, but partition usually wipes the data completely.  Especially when installing a new operating system onto the partition.

What your son did is quite normal.  Windows hangs, so reboot.  How large was the hard drive?  It's hard to understand how to install Ubuntu twice (and not remember doing it!).  That would explain 2 swap partitions.  

Normally Ubuntu installs and detects a Windows partition and puts the correct entry into GRUB, the boot loader.  Of course, this won't happen if the Windows partition gets wiped and Ubuntu is   installed in the same space where the Windows files were located.

Normally, Ubuntu sees the Windows partition, squishes it to half size--safely moving data into the small partition.  Then adds a Linux partition (EXT3) on the second half of the disk, also adds a small swap partition.  Ubuntu goes onto the second partition, not touching Windows.  

I have done this several times without a problem.  However, to someone who is not aware of the consequences--there is an option to "Wipe the entire disk and install Ubuntu".  This does exactly that.

Perhaps the second installation pushed the first installation into 1/2 the disk, then installed a second copy of Ubuntu.  That would explain the second swap drive.

It looks like your data is toast.

When I was 6, I put sand in the gas tank of my neighbor's lawn mower.  Kids do dumb things.

---

### Post by ddrichardson on 2007-09-17
There are data recovery software for [Linux]("http://quick-recovery-for-linux-a-data-recovery-software.unistal-systems-pvt-ltd.qarchive.org/"). It depends on how much data hasa been written to the drive. 

Formatting (unless you overwrite with 0's) doesn't remove data it only changes structures and file tables. Make an image of the drive, so that you don't make things worse.

Unfortunately most systems (as tgalati4 said) are aimed at NTFS and Fat32. You could try:
1. Image the disk using [System Rescue CD]("http://www.sysresccd.org/Main_Page")
2. Format to NTFS
3. Run a data recovery program

You'd be surprised how much recovery programs can recover. It's generally only a hassle because the filenames are lost so you need to spend some time working out what the recovered data actually is.

---

