---
title: "How to get Ubuntu to boot on a HDD with extended partitions??"
date: 2007-02-20
forum: General Help
---

### Post by billdotson on 2007-02-20
When I was reinstalling Ubuntu I created a 25GB ext3 partition, a 256MB swap, then I did an extended partition with 6 (I think) logical FAT32 partitions and one 25GB xfs.  Then I made a 20-25GB NTFS partition.   

       All this was done on an USB 2.0 external 279GB HDD.  When I got to the screen of installation where it shows the drives and where you assign them names like root, /, var, media, etc.  I set the Ubuntu partition to / the 256MB to swap and went down and added all of the FAT32  partitions and teh xfs one in order going /media/usbdisk1 , /media/usbdisk2 and so on until there were not anymore drives left to be assigned except for the ntfs.  

    Since Ubuntu is on an external drive to get it to boot while the internal drive is plugged in I have to go to /boot/grub/menu.lst and /etc/fstab and change all of the sda entries to sdb entries.  Doing that works when I have no extended partitions.  But when I had the extended partition with all of the logical ones Ubuntu would not boot.

I went in and changed all the sda entries I could find in both files to sdb and I thought I had it working but when I tried to boot Ubuntu I got an error that GRUB couldn't read it or something of that nature.  The reason I want almost all my space on FAT32 partitions is because I also use Windows and I want it where I can access and modify my files from either OS.  (I know it is possible to have read and write support on NTFS but it is experimental and I don't want to lose any files)
 
Right now I just have 4 primary partitions of ext3, swap, FAT32, and then an NTFS (which is like 250GB.. :(  because I couldn't get teh logical FAT32's to work)

How do I fix this problem so that I have my external HDD setup the way I want it?

Thank you.

---

### Post by dcstar on 2007-02-20
> **billdotson said:**
> When I was reinstalling Ubuntu I created a 25GB ext3 partition, a 256MB swap, then I did an extended partition with 6 (I think) logical FAT32 partitions and one 25GB xfs.  Then I made a 20-25GB NTFS partition.   

       All this was done on an USB 2.0 external 279GB HDD.  When I got to the screen of installation where it shows the drives and where you assign them names like root, /, var, media, etc.  I set the Ubuntu partition to / the 256MB to swap and went down and added all of the FAT32  partitions and teh xfs one in order going /media/usbdisk1 , /media/usbdisk2 and so on until there were not anymore drives left to be assigned except for the ntfs.  

    Since Ubuntu is on an external drive to get it to boot while the internal drive is plugged in I have to go to /boot/grub/menu.lst and /etc/fstab and change all of the sda entries to sdb entries.  Doing that works when I have no extended partitions.  But when I had the extended partition with all of the logical ones Ubuntu would not boot.

I went in and changed all the sda entries I could find in both files to sdb and I thought I had it working but when I tried to boot Ubuntu I got an error that GRUB couldn't read it or something of that nature.  The reason I want almost all my space on FAT32 partitions is because I also use Windows and I want it where I can access and modify my files from either OS.  (I know it is possible to have read and write support on NTFS but it is experimental and I don't want to lose any files)
 
Right now I just have 4 primary partitions of ext3, swap, FAT32, and then an NTFS (which is like 250GB.. :(  because I couldn't get teh logical FAT32's to work)

How do I fix this problem so that I have my external HDD setup the way I want it?

Thank you.

Without the external drive plugged in Grub will see the internal drive as "0", when the external one is plugged in I'm guessing that it becomes drive "0" and the internal drive "1" - this will confuse Grub no end!

You basically need to duplicate all of the Grub entries and have two sections - one for only one drive (internal), and another for both drives available.

You then need to manually modify the Grub entries for the correct drive number and /sd designations - then you should (in theory) be able to boot off the correct entry for the particular hardware configuration you are using.

I had to do this when I created a USB stick install, the generated Grub designations from the install were wrong when I actually booted off the USB device - so a bit of editing of the menu.lst file fixed that issue.

---

### Post by billdotson on 2007-02-21
what do you mean make multiple GRUB entries??  Could you please explain I really didn't understand

---

### Post by dcstar on 2007-02-22
> **billdotson said:**
> what do you mean make multiple GRUB entries??  Could you please explain I really didn't understand

At the end of you Grub menu.lst there are a host of lines (in groups) to boot each available system, these will have designations like hd (0,0) and /dev/sda in them.

If you want to boot off additional drives, or if you plug in another physical drive that makes those previous settings incorrect, then you may have to duplicate all of those entries and manually change the second set to suit the changed hardware.

For instance, the hd (0,0) may become hd (1,0) when the other drive is there. The /dev/sda may actually be /dev/sdb when the other drive is there (these are guesses, but they may be correct).

You can add as much as you like to your menu.lst file and experiment with the settings, either they will work or they won't.

You can also interrupt the Grub boot-up and enter commands to help you identify how Grub is recognising your hardware (you will have to search out this stuff, it is quite detailed), and that can assist greatly in tweaking your menu.lst file to get it working.

---

