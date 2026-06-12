---
title: "GRUB  Error 15"
date: 2007-12-20
forum: General Help
---

### Post by scottrocket on 2007-12-20
i deleted the partition i had ubuntu installed on using partitionmagic and upon restart GRUB would error and my computer would lock up,  so i tried using supergrub and was having issues with it but i figured out the problem, and got my computer to boot up.  Now I have another issue/question, every time that i restart my computer is it going to try to load GRUB and i'll have to put in the disk to get past that?  how would i make make the computer not attempt to load GRUB upon startup?  that last question i guess only matters if my partition stuff worked correctly, still waiting for it to finish the recombining of my partitions and stuff.

thanks
-scott


everything seems to have worked correctly for the partitioning, so the only problem i have is making the boot process forget that i ever had multiple OS's and stop trying to load GRUB...any assistance there would be appreciated.

---

### Post by tgilber1 on 2007-12-20
I recommend saving yourself all this grief by just using grub rather than partition magic as your primary bootloader.  If my memory serves me right, the steps are below making things works

What should happen if Partition magic is installed on the MBR, the PC shouldl boot to bootmagic (part of PartitionMagic).  Bootmagic will provide a timed-prompt screen to choose the OS to boot into, i.e., Windows or Linux.  If Linux partition is chosen, it will call GRUB will provide a similar screen to choose OS, finally booting into Linux.

GRUB has two options for installing, MBR or root partition.  

Using GRUB on the MBR, saves time, money, and hassle.  To install on MBR follow the instructions below

1.  Get to the GRUB screen by typing "grub" at the command line - either through a recovery  or emergency boot disc - provided by distribution
2.  Type root (hd?,?) ? is a number.  ex.  root (hd0,0).  If unsure, use the tab button to view options
3.  After finding a disk and partition with root (hd?,?) command
4.  Type "kernel /" and tab to verify correct partition, the files should be the same as what is in the /boot directory -- it should have the kernel image files
5.  Verify and select correct root partition, which was done in step 4
6.  Type "setup (hd?)"  ex. setup (hd0) to write GRUB to the MBR of disc.  Voila, you should be able to Linux without Partition Magic.

If PartitionMagic is the choice, then run the distribution setup and install GRUB on the root partition rather than the MBR.  You may have to run Windows fdisk /MBR or PartitionMagic again, if the MBR is really hosed.  I do not know how Windows Vista handles this situation.

---

