---
title: "Disk Partitioning and Ubuntu bootloader problem"
date: 2013-09-25
forum: General Help
---

### Post by ray5 on 2013-09-25
I have a new Samsung external USB disk on which I wish to install 3 Linux distros; Ubuntu 12.04, Lubuntu 13.04 and Mint.  I have partitioned the Samsung USB drive using Gparted, creating 2 primary and 1 extended partition with the extended partition containing several logical partitions.  So I have  /dev/sdc        Samsung 1TB drive /dev/sdc1      ntfs partitioned /dev/sdc5      ext2 partition for Ubuntu 12.04 /dev/sdc6      ext2 Partition for Lubuntu 13.04 /dev/sdc7      ext2 Partition for Linux Mint /dev/sdc8      ext2 Data partition  /dev/sdc2      Linux Swap  I want to allocated to swap space partition to be used by each of the Linux o/s.  The Ubuntu 12.04 Installation failed at the end    with error message   “Unable to install GRUB in /dev/sdc5”  I tried setting the partition to choose /dev/sdc as the partition to install the bootloader into,  but the same error message was again the result.  What do I do to get the bootloader to install on this disk ( an external USB drive ) ?  Thanks Ray NB the os on the internal drive is Windows Vista.

---

### Post by nerdtron on 2013-09-25
/dev/sdc1      ntfs partitioned
 /dev/sdc5      ext2 partition for  Ubuntu 12.04 
/dev/sdc6      ext2 Partition for Lubuntu 13.04 
/dev/sdc7       ext2 Partition for Linux Mint 
/dev/sdc8      ext2 Data partition   
/dev/sdc2      Linux Swap

Some notes:
Please don't use ext2 format partitions for data/OS files. ext4 is the recommended filesystem.
Also, I suggest you put the ntfs partition on the end of the drive, meaning, put the linux partitions first and the last partition is the ntfs partition.
Install the boot loader on the drive itself which is /dev/sdc
And a lot would be better if you REMOVE the internal drive and boot Ubuntu (either live cd or USB) and then plug the external drive. This way, Ubuntu will be forced to detect/install on the external drive.

---

