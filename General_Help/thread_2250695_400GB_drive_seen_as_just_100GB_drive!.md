---
title: "400GB drive seen as just 100GB drive!"
date: 2014-10-30
forum: General Help
---

### Post by sim085 on 2014-10-30
Hello,

fdisk -l is reporting that one of my drives is only 103.1GB large when in fact this is a 400GB drive. Yesterday I formatted the drive and it reported as size of around 390GB. I did not bother much about this because I know that drives actual size is always less than what is reported on the label. I used fdisk /dev/sda to delete all partitions on the drive (it had four), I created one partition (primary) the size of the drive. Then I format this to ext4. I then updated /etc/fstab to mount the drive on start up (using /dev/disk/by-uuid to get uuid value of drive). I reboot ... all ok.

This morning I switched on the pc and it did not want to boot. I got a message saying that this drive could not be mounted. I looked for the drive in /dev/disk/by-uuid and it was not there (only the disk where my OS is installed is listed). I then ran fdisk -l and I can see the drive. However this is reported as just 103.1GB! 

Why could this be?

---

### Post by sim085 on 2014-10-30
I remembered from a past problem that this could be because of some partition information written on first part of drive. I ran the dd command and stopped it after some time! This drive was used for Windows before. Does this mean that dd command must always be used?

dd if=/dev/zero of=/dev/sda iflag=nocache oflag=direct bs=4096

---

### Post by oldfred on 2014-10-30
Is this an external drive?
       [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
USB adapter may show drive as 1/8 size, use SATA port for 4K drives

If only a Linux drive, try gpt partitioning.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

If you want it to be a bootable drive with grub. 
If using gpt with BIOS create a 1MB bios_grub partition with no format.

---

