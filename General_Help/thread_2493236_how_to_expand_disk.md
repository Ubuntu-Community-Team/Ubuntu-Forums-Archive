---
title: "how to expand disk"
date: 2023-12-07
forum: General Help
---

### Post by den-denzel on 2023-12-07
Good day, I don't know how to increase the disk on which the operating system is installed, who can help.  Ubuntu 22.04.

---

### Post by vanadium on 2023-12-07
That is done with a partition editor, e.g. Disks that comes by default with the Ubuntu desktop, or gparted, that can be installed. If changing the size of the partition disk, that partition cannot be in use. In that case, you can do the operation from within a live session started from an installation USB or DVD.

---

### Post by Rubi1200 on 2023-12-07
You need to give us more information if we are to help.

Open a terminal with Ctrl+Alt+T and show us the output from these commands:

```
sudo fdisk -l
```

and

```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

When replying, click on Go Advanced >> paste the output >> highlight the text and click on the # icon to wrap with code tags.

As vanadium rightly pointed out, you cannot perform operations on disks or partitions that are mounted.

The safest way is from a live media such as USB.

---

### Post by den-denzel on 2023-12-07
250 GB SSD for recording the Ubuntu image, I allocated 50 GB, I'm interested in how to increase this partition?

---

### Post by yancek on 2023-12-07
I'd suggest you respond to the questions asked in the above post 3 as there is no way you can get specific instructions when you are giving only general information  You could start by using gparted and reading through the section of the manual at the link below.  Resizing is under Advanced Partition Actions.  The fdisk -l output would provide specific information on your drive and you should then inform us of exactly what you want.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by den-denzel on 2023-12-07
fdisk -l
```

Device Start End Sectors Size Type
/dev/sda1 2048 206847 204800 100M EFI system
/dev/sda2 206848 239615 32768 16M Microsoft Reserved
/dev/sda3 239616 101423209 101183594 48.2G Microsoft Core Data
/dev/sda4 101425152 102399999 974848 476M Linux file system
/dev/sda5 102400000 428435455 326035456 155.5G Microsoft Core Data
/dev/sda6 428435456 500115455 71680000 34.2G Linux file system
/dev/sda7 500115456 500117503 2048 1M Linux file system




Disk /dev/sdb: 232.89 GiB, 250059350016 bytes, 488397168 sectors
Disc model: TS250GMTS425S
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes
Disk label type: gpt
Disk ID: 7EA3DD56-7000-4EC0-8FEE-5CBAC3104DCE


Device Start End Sectors Size Type
/dev/sdb1 2048 206847 204800 100M EFI System
/dev/sdb2 206848 239615 32768 16M Microsoft Reserved
/dev/sdb3 239616 180123647 179884032 85.8G Microsoft Core Data
/dev/sdb4 180123648 180125695 2048 1M Microsoft, core data
/dev/sdb5 180125696 487319055 307193360 146.5G Microsoft Core Data
/dev/sdb6 487321600 488394751 1073152 524M Microsoft core data




Disk /dev/loop8: 73.9 MiB, 77492224 bytes, 151352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 240.32 MiB, 251994112 bytes, 492176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 240.32 MiB, 251990016 bytes, 492168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop11: 164.82 MiB, 172830720 bytes, 337560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop12: 349.7 MiB, 366682112 bytes, 716176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop13: 485.52 MiB, 509100032 bytes, 994336 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop14: 496.98 MiB, 521121792 bytes, 1017816 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop15: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop16: 131.21 MiB, 137588736 bytes, 268728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop17: 129.67 MiB, 135966720 bytes, 265560 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop18: 2.45 MiB, 2572288 bytes, 5024 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop19: 35.59 MiB, 37322752 bytes, 72896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop20: 12.32 MiB, 12922880 bytes, 25240 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop21: 40.84 MiB, 42827776 bytes, 83648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop22: 40.86 MiB, 42840064 bytes, 83672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Input-output size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop23: 452 KiB, 462848 bytes, 904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop24: 413.94 MiB, 434049024 bytes, 847752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes




Disk /dev/loop25: 414.13 MiB, 434241536 bytes, 848128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (min/optimal): 512 bytes / 512 bytes

```

---

### Post by den-denzel on 2023-12-07
df -hT -x sqashfs -x tmpfs -x devtmpfs

```

&#1060;. &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;     &#1058;&#1080;&#1087;   &#1056;&#1086;&#1079;&#1084;   &#1042;&#1080;&#1082;  &#1044;&#1086;&#1089;&#1090; &#1042;&#1080;&#1082;% &#1079;&#1084;&#1086;&#1085;&#1090;&#1086;&#1074;&#1072;&#1085;&#1080;&#1081; &#1085;&#1072;
/dev/sda3      ext4   48G   27G   19G  59% /
/dev/sda1      vfat   96M   32M   65M  33% /boot/efi




```

---

### Post by grahammechanical on 2023-12-07
I am confused.

> /dev/sda3 239616 101423209 101183594 48.2G Microsoft Core Data

> /dev/sda3      ext4   48G   27G   19G  59% /

What is the sda3 partition? Is a partition used by Microsoft Windows? Or, is it the partition with Ubuntu installed?

To enlarge one partition we have to shrink some other partitions. This will create unallocated space. But it may be in the wrong place. So, we have to move other partitions into the unallocated space so that the unallocated space moves closer the partition we want to expand. We need the unallocated space either in front of or behind the partition we want to expand. Then we can expand the partition to the left or the right to use up the unallocated space.

If you open the Disks utility you will get a visual representation of the partitions on both of your drives. You will find out the size of the partition, the Filesystem (Linux or Microsoft type) and if it is sda1, sda2, sda3 and so on.

Draw a copy of the picture that Disks utility shows you. It will help you to when using GParted from a Ubuntu live session.

Please remember, that it is best if we use Microsoft tools to work with Microsoft partitions and Linux/Ubuntu tools to work with Linux partitions.

Regards

---

### Post by yancek on 2023-12-08
Your Linux filesystem partitions are on sda.  If you look at the start and end sectors for each, you will see there is no room to expand any of them with the possible exception of sda7.  We can't know if that is possible because you left off the first part of the fdisk output for sda which tells total sectors.  Based on the end sector of sda7, I doubt there is any room to expand on that 250GB drive and you would need to either eliminate or shrink another partition.

You indicated in an earlier post that you created a 50GB partition for Ubuntu but fdisk shows the largest Linux partition as 34.2GB.  One possible solution if sda5 is a data partition for windows and sda6 is Ubuntu, would be to boot windows and use Disk Management to resize/shrink that partition from the right (the end of the partition) to get free space on which to expand the Ubuntu partition.  You could then boot your Ubuntu 'live' usb and use gparted to expand sda6 (the Ubuntu partition) to the left.  The problem with this is that the boot files for the Ubuntu Grub bootloader will be at the beginning of that partition and will be moved which could create a problem in booting.  You should see a message to that effect if you use gparted to do this.

Best to post more specific details on what you want to expand/shrink.

---

