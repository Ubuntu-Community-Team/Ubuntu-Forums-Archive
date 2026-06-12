---
title: "Removing partition"
date: 2007-06-23
forum: General Help
---

### Post by Silenus on 2007-06-23
My friend has just installed ubuntu 7.04 fiesty, and copied his music and movies over to fiesty, and wants to remove windows completely, the partition etc. But I don't know how to go about removing the windows partition, I know you can use gparted, but I don't know the steps. 

Thanks in advance

---

### Post by Happy_Man on 2007-06-23
You just boot up the LiveCD, open Gparted, and delete the partition by right-clicking and choosing "delete partition."

---

### Post by Silenus on 2007-06-23
Well he already has linux installed and gparted doesn't seem to work for him, gparted: error while loading shared libraries: libgtkmm-2.4.so.1: cannot open shared object file: No such file or directory
I tried to install libgrkmm, and it gave errors to, and so did ssh, think the live cd would have it but the install wouldnt?

---

### Post by Happy_Man on 2007-06-23
No, you don't have to reinstall, you can just use the LiveCD Gparted to delete the partition (go to System -->Administration --> GNOME Partition Editor on the LiveCD) and then shut it down and reboot off the HDD to Ubuntu as usual.

---

### Post by Silenus on 2007-06-23
Ok one problem though he doesn't know how to tell which is windows, I told him fat32 would be the windows install, that's correct right?

---

### Post by bigboy_pdb on 2007-06-23
You should back up everything that you need or want to keep to an external hard drive or some CD-RWs before proceeding in case something goes wrong.

Type mount to list the partitions that you have mounted and their mount points. The windows partition should look something like this (if it is mounted):
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)

The windows parition will most likely be the first partition on the first hard drive (which will be something like /dev/sda1 or /dev/hda1) and it should be of type ntfs if your windows file system is an NT file system (Windows 2000 or XP) or of type vfat if it is a FAT32 file system (Windows 95, 98, and ME). It is important that you know which partition and hard drive it is on before you attempt to remove it.

Before you reformat the partition you must unmount it. So in a terminal ('Applications' -> 'Accessories' -> 'Terminal') type 'sudo umount /dev/sda1' where /dev/sda1 is the device for the hard drive partition that your Windows is on. The 'sudo' indicates that you want to run the command 'umount /dev/sda1' as the root user (if you don't run the command as root, the drive won't be unmounted). At the prompt type 'sudo fdisk /dev/sda' to perform fdisk operations on the first hard drive (where /dev/sda should the hard drive that your Windows was installed on).

NOTE: If at any point while you are running fdisk you make a change that you are unhappy with you can type 'q' to quit without saving the changes.

fdisk will now be running. Type 'm' to see a list of commands. Type 'p' to list your parititions. You should see the device affiliated with the partition that windows was installed on (that you previously unmounted). Use 'd' to delete that partition. When it asks for a partition number from [1 to n] enter the number that corresponds with the device of the windows partition (for example you would type '1' if the device corresponding to the Windows partition is '/dev/sda1'). Type 'p' again to make certain that the correct partition has been removed (remember that if you've made a mistake you can type 'q' to quit without saving and run fdisk again). Type 'n' to add a new parition and go through the steps to add the new partition. Type 'p' to check your new table. Type 't' to select the type of file system for the parition and select that partition then enter the number for the filesystem that you want. You can type 'L' to list the types of file systems ('83' is Linux and 'c' is FAT32). Type 'p' to check your changes one more time. If you are happy with your changes, type 'w' to write the new parition and exit, otherwise type 'q' to quit without saving the changes.

The partition is has now been set up, but you need to make the a new file system on the partition. You'll have to use 'mkfs' to do this. For more information on this program you can use the man page for 'mkfs' (which can be viewed by typing 'man mkfs'). To create a linux ext3 file system use 'sudo mkfs.ext3 -L labelname /dev/sda1' or to create a FAT32 file system use 'sudo mkfs.vfat -L labelname /dev/sda1' (where labelname is the label that you want the partition to have and /dev/sda1 is the device that corresponds to the partition where the filesystem is to be made).

NOTE: You can only use mkfs.ext3 with a 'Linux' partition and mkfs.vfat with a 'FAT'/'FAT32' partition.

Some other programs for creating filesystems that you can look up the man pages for are:
mkfs.reiserfs
mkfs.msdos
mkfs.vfat
mkfs.ext3
mkfs.ext2
mkfs.cramfs
mkfs.minix

The reason why I mention making FAT32 file systems is because Linux and Windows can read from and write to FAT32 file systems, and most external hard drives use FAT32 file systems (meaning if you want to partition your external hard drive you might want to use one or more FAT32 file systems).

---

