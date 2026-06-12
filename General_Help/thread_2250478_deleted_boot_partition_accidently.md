---
title: "deleted boot partition accidently"
date: 2014-10-28
forum: General Help
---

### Post by luke40 on 2014-10-28
I  deleted the boot partition accidently, now my pc shows

error: file '/grub/i386-pc/normal.mod' not found.
Entering rescue mode...
grub rescue>

every time when I boot. The partition which store the data is intact.
Any kindly help will be much appreciated.

---

### Post by SuperFreak on 2014-10-28
You might want to run Boot Repair from the Live USB or DVD, it is available at [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by yancek on 2014-10-28
If you deleted the boot partition, you can't boot until you reinstall the Grub boot files as well as the kernel and initrd files.  When you say the partition which stores data is intact, do you mean the root filesystem partition?  Are you using Ubuntu or one of its derivatives and which release?  You should be able to mount the boot partition after re-creating it and copy the files you need there.  Post the output of the command:  sudo fdisk -l(Lower Case Letter L in the command) so we can see your drive/partition info.  Also, the output of parted -l

---

### Post by luke40 on 2014-10-31
> **SuperFreak said:**
> You might want to run Boot Repair from the Live USB or DVD, it is available at [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")


Thnaks for help.

My version is 14.04 and the repair dvd is 13.04 so I got problems after many times of trying. Now the "grub" prompt don't even appear and the screen says "missing operating system!"

Still thanks very much.

---

### Post by luke40 on 2014-10-31
> **yancek said:**
> If you deleted the boot partition, you can't boot until you reinstall the Grub boot files as well as the kernel and initrd files.  When you say the partition which stores data is intact, do you mean the root filesystem partition?  Are you using Ubuntu or one of its derivatives and which release?  You should be able to mount the boot partition after re-creating it and copy the files you need there.  Post the output of the command:  sudo fdisk -l(Lower Case Letter L in the command) so we can see your drive/partition info.  Also, the output of parted -l


Thank you very much.

Yes, it's the root filesystem wasn't deleted. How to reinstall the the grub boot files and kernel and initrd files?

I am using ubuntu 14.04. How to recreat and mount the boot partition and copy the necessary files?

Since I can't boot now so I have to use the installation disk, but now some sector of it was corruptted so I must manage to download another copy, geeze!

I will do my best to get the partition info as you said and look forward for your advice.

Thank you very much again.

---

### Post by sisco311 on 2014-10-31
Hi, luke40!

Was  the whole boot partition deleted or just the files on it?

Please post your [Boot-Info]("https://help.ubuntu.com/community/Boot-Info"). You can use your existing boot repair disk to create it.

---

### Post by yancek on 2014-10-31
The link below, beginnig in Section 2.2, explains several methods of reinstalling Grub2.  Since you also deleted the kernel and initrd, you would first need to mount whichever partition on which the boot files were on your hard drive, then create a boot directory and then copy the vmlinuz and initrd files there before trying to install Grub2.  In all likelihood, you will need to eventually use the chroot method (Section 2.2.5) to accomplish this.   

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by SuperFreak on 2014-10-31
Sorry boot repair didn't work out. If this has not been mentioned already then BACKUP any personal non system files

---

### Post by oldfred on 2014-10-31
Boot-Repair also has a full uninstall and reinstall of grub. I think it also pulls in the latest kernel but if not run that while in the middle of the reinstall of grub2.

when chrooted you can run all these commands, anything after the # is comment, do not copy comments.

 #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

---

### Post by luke40 on 2014-11-01
[SIZE=2]Hi, SuperFreak, yancek, sisco311, and oldfred,

Thank you.

Before I take any action I would like to describe my situation as well as provide the partition information. Yesterday when I tried many times including reinstalling grub and MBR via boot-repair-disk, every time it told me that I should enable the 14.04 repository that contains the necessary files, but I don't know how to enable it.

Every time the default boot parition would be set to sda1 and I always changed it to sda5. The partition info are as follows:

[COLOR=#006400]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cb032

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   390635519   195316736   83  Linux
/dev/sda2       390637566   976771071   293066753    5  Extended
/dev/sda5   *   390637568   968386559   288874496   83  Linux
/dev/sda6       968388608   976771071     4191232   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  200GB  200GB   primary   ext4
 2      200GB   500GB  300GB   extended
 5      200GB   496GB  296GB   logical   ext4            boot
 6      496GB   500GB  4292MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!  [/COLOR]


In fact, the 296G block was unallocated at least before I tried the boot-repair-disk and I just found the boot mark is there now!
I don't know where the boot parition should be exactly. That's why I deleted it because I seemed seeing it located in the extend parition and thought it belong to the usb storage. The 200G block is the storage I adopted when I installed ubuntu 14.04. Should the boot partition also be there? But the root filesystem is already there, so does it means that now the entire 200G belong to the root filesystem and I have to partition it in order to reinstall boot partition? Is it dangerous and what should I do?

Thank you all.
[/SIZE]

---

### Post by yancek on 2014-11-01
> [SIZE=2]In fact, the 296G block is an unused(not even be created) and I just found the boot mark is there now![/SIZE]

You don't need the boot or active indicator for a Linux system as that is only necessary for windows.  Doesn't matter.


> [SIZE=2]Although I like Linux I am still a novice after so many years and I don't know where the boot parition should be exactly.[/SIZE]

First, you do not "need" a separate boot partition and you can create a separate boot directory in the primary filesystem for Ubuntu with a Grub sub-directory and install there.  If you had a separate boot partition and deleted it, it is usually at the beginning of the drive and you should be able to see unallocated space with this command:

```
sudo parted /dev/sda print free
``` 

It doesn't seem you have enough space at the beginning of the drive to have had a separate boot partition.

---

### Post by luke40 on 2014-11-01
> **yancek said:**
> you do not "need" a separate boot partition and you can create a separate boot directory in the primary filesystem for Ubuntu with a Grub sub-directory and install there. 

The result of the command is:

[COLOR=#006400]ubuntu@ubuntu:~$ sudo parted /dev/sda print free
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
        32.3kB  1049kB  1016kB            Free Space
 1      1049kB  200GB   200GB   primary   ext4
        200GB   200GB   1048kB            Free Space
 2      200GB   500GB   300GB   extended
 5      200GB   496GB   296GB   logical   ext4            boot
 6      496GB   500GB   4292MB  logical   linux-swap(v1)
        500GB   500GB   1073kB            Free Space
[/COLOR]
I don't remember if I created a separate boot partition. So, if I want to access my data, what is the best way? Can I install the boot partition in the primary partition? Is there any way to access the root filesystem?

Thanks.

---

### Post by yancek on 2014-11-01
You don't have enough free space anywhere to create a separate boot partition except on sda5 and it would be a waste of space to have a 296GB boot partition.  Most systems when creating a boot partition will make them 100-200MB but with newer systems and frequent kernel updates now 1GB.  As I indicated above, there is no "need" to have a separate boot partition and you can put the boot files on your / (root) filesystem partition which is sda1.  I haven't used the boot repair software so I'm not sure what it will do in this case.  You might review the post by oldfred above as he seems to be very familiar with the software and what it does.  If that doesn't work, you can use the DVD of Ubuntu you have to create aa mount point for sda1, mount it and then copy the kernel and initrd files there as well as the Grub files.  You would then need to use the chroot method explained in the link I posted earlier to update grub.

---

### Post by oldfred on 2014-11-01
If unsure of how your system is configured, best to post a link to the summary report from Boot-Repair.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by luke40 on 2014-11-01
The attachment is the image from the GUI gparted.

Now I remember it seems that there was a separate boot partition in the extended sda5. As you can see, the swap partition is 4G and the used space is 5.45G, so it seems I allocated 1G to the boot partition. It is included in the 275G (sda5) now. Also my computer didn't work just after i deleted it (boot partition).

May I re-divide sda5 and make 1G space for boot partition and making any operation there?

If my computer configuration was such, will it also work if I put the boot files on the root filesystem now? If it does then it will be much simpler than the former method, right?

---

### Post by oldfred on 2014-11-01
Actually better not to have a separate /boot partition for most desktops.
Servers or server configurations with RAID or LVM may need a boot partition and some very old systems need one in the first 100GB of a drive. Or have a smaller / (root) fully within the first 100GB.

If you do not tick the separate /boot partition and run the full uninstall reinstall of grub, it should install grub & kernel into the /boot folder inside /. But you may have to manually delete the entry in fstab for your /boot partition.

---

### Post by luke40 on 2014-11-05
I used boot-repair-disk plus oldfred's command line codes and the advice as yancek said and now my system can boot again.

Thanks.

---

