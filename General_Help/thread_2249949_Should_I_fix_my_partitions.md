---
title: "Should I fix my partitions?"
date: 2014-10-25
forum: General Help
---

### Post by RangerK on 2014-10-25
I had trouble installing a Windows / Ubuntu dual boot on my Dell Inspiron 5423.  Ubuntu didn't like the Sata drive.  I had a friend try to do it for me, but he also failed, and returned my computer with Windows on the Sata drive, and Ubuntu 14.04 on the HD.

I've been using it a couple month.  I don't want to reinstall, but I noticed that the partitions look strange.  I think some of them are not used at all.  Should I try to modify things?  Is it safe to do so without having to reinstall?

Windows can see and write to the SDA2 partition, "New Volume."

In the Ubuntu Launcher there is 
SDA2, SDA1, SDA5 (grub), SDA 7 (the strange one I can't write to), SDB1 (windows)

There seems to be no SDA4, but there's a 5, 6, 7, 8, and 9.

I can't write to SDA7 (203 Gb) from Ubuntu.  It has a "username" folder with two broken links: "Access-Your-Private-Data.desktop" and "README.txt".  Is this left over from a windows install?

SDA6 (2.8 Gb) and SDA9 (3.9 Gb) are both Linux swap / Solaris.  Do I need both?

SDA3 is just 1k.

==========================================

Here are the results of commands to view the partitions:

```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```


```
NAME   FSTYPE   SIZE MOUNTPOINT LABEL
sda           465,8G            
&#9500;&#9472;sda1 ntfs     100M            &#1047;&#1072;&#1088;&#1077;&#1079;&#1077;&#1088;&#1074;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1086; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1086;&#1081;
&#9500;&#9472;sda2 ntfs   244,1G            New Volume
&#9500;&#9472;sda3            1K            
&#9500;&#9472;sda5 ext4     1,4G            
&#9500;&#9472;sda6          2,8G            
&#9500;&#9472;sda7 ext4   189,4G            
&#9500;&#9472;sda8 ext4    24,1G /          
&#9492;&#9472;sda9 swap     3,9G [SWAP]     
sdb            29,8G            
&#9492;&#9472;sdb1 ntfs    29,8G            
sr0            1024M  

```

==========================================

```
lsblk
```

```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465,8G  0 disk 
&#9500;&#9472;sda1   8:1    0   100M  0 part 
&#9500;&#9472;sda2   8:2    0 244,1G  0 part 
&#9500;&#9472;sda3   8:3    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0   1,4G  0 part 
&#9500;&#9472;sda6   8:6    0   2,8G  0 part 
&#9500;&#9472;sda7   8:7    0 189,4G  0 part 
&#9500;&#9472;sda8   8:8    0  24,1G  0 part /
&#9492;&#9472;sda9   8:9    0   3,9G  0 part [SWAP]
sdb      8:16   0  29,8G  0 disk 
&#9492;&#9472;sdb1   8:17   0  29,8G  0 part 
sr0     11:0    1  1024M  0 rom  
```

==========================================

```
sudo fdisk -l
```

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xb9d6cf0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   512206847   256000000    7  HPFS/NTFS/exFAT
/dev/sda3       512208894   976771071   232281089    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda5       512208896   515136630     1463867+  83  Linux
/dev/sda6       573732864   579590143     2928640   82  Linux swap / Solaris
/dev/sda7       579592192   976771071   198589440   83  Linux
/dev/sda8       515137536   565614591    25238528   83  Linux
/dev/sda9       565616640   573728767     4056064   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
255 heads, 63 sectors/track, 3892 cylinders, total 62533296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6d96fb58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    62529535    31263744    7  HPFS/NTFS/exFAT

```

==========================================

```
/media/user$ ls -la
```

```

total 36
drwxr-x---+ 7 root root  4096 &#1078;&#1086;&#1074; 25 22:47 .
drwxr-xr-x  3 root root  4096 &#1074;&#1077;&#1088; 24 11:17 ..
drwxr-xr-x  5 root root  4096 &#1089;&#1077;&#1088; 11 22:39 1673f875-f53f-49ab-a12a-84a39803bcf9
drwxr-xr-x  4 root root  4096 &#1089;&#1077;&#1088; 17 21:55 4b69b6b5-67dc-40c5-86dc-0101f31aee44
drwx------  1 user user 12288 &#1078;&#1086;&#1074; 24 01:32 DAE88D27E88D034D
drwx------  1 user user  4096 &#1078;&#1086;&#1074; 24 02:17 New Volume
drwx------  1 user user  4096 &#1089;&#1077;&#1088; 11 13:37 &#1047;&#1072;&#1088;&#1077;&#1079;&#1077;&#1088;&#1074;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1086; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1086;&#1081;

```

==========================================

Thanks for taking the time to look at this.  Any advice is appreciated.

---

### Post by mikewhatever on 2014-10-25
You are right, there are way too many Linux partitions (only one swap is needed), I'd suggest reinstalling, and while at it, delete all except the NTFS partitions. Messing with partitions without reinstalling is pretty safe, if you know how, but not bullet proof. Besides, you'll need to deal with the bootloader, which more often is not worth it.

---

### Post by oldfred on 2014-10-25
Since you have two swaps, I am assuming you use auto install twice. And it just shrank the first install to make space for second install.
Is sdb just your flash drive?

Your sda1 is Windows boot, I assume sda2 "New Volume" is your main Windows partition or c: "drive".
Your sda3 is the extended partition which is a primary partition but acts like a container for all the logical partitions sda5 and above.

If you want to try to repair one of your installs download and run this. 
Otherwise you can just use gparted (not Windows) to erase your logical partitions and reinstall.

You can just run the summary report and post link to see all the details.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

---

### Post by RangerK on 2014-10-25
> **oldfred said:**
> 
Is sdb just your flash drive?

Your sda1 is Windows boot, I assume sda2 "New Volume" is your main Windows partition or c: "drive".
Your sda3 is the extended partition which is a primary partition but acts like a container for all the logical partitions sda5 and above.


sdb is the SATA drive with Windows.

Sda1 is my Linux boot.  It's only 100 MB.

Sda2 is a partition accessible by both windows and ubuntu.

I think my main Linux partition is Sda8.  

When I run the command "df", I get: 

```
/dev/sda8       24711288 7487908  15945072  32% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1945096       4   1945092   1% /dev
tmpfs             391176    1164    390012   1% /run
none                5120       0      5120   0% /run/lock
none             1955876     156   1955720   1% /run/shm
none              102400      48    102352   1% /run/user
```

---

### Post by oldfred on 2014-10-25
Then root is sda8.

Post link from Boot-Repair's summary report.

---

### Post by prshah on 2014-10-25
> **RangerK said:**
>  I've been using it a couple month.  I don't want to reinstall, but I noticed that the partitions look strange.  I think some of them are not used at all.  Should I try to modify things?  Is it safe to do so without having to reinstall?

SDA 7 (the strange one I can't write to)

There seems to be no SDA4, but there's a 5, 6, 7, 8, and 9.

I can't write to SDA7 (203 Gb) from Ubuntu.  It has a "username" folder with two broken links: "Access-Your-Private-Data.desktop" and "README.txt".  Is this left over from a windows install?

SDA6 (2.8 Gb) and SDA9 (3.9 Gb) are both Linux swap / Solaris.  Do I need both?


sda3 is an extended partition, which holds other partitions (5,6,7,8,9). it is supposed to be just 1K. Non-GPT partitioning (which is what you have) allows for 4 primary partitions; however, if you need more, at least one primary partition can be made as an extended partition, which can then have a number of "logical" partitions (I think 128 is the limit, not sure).

Note that if you force-remove sda3, you will LOSE sda 5,6,7,8,9 !

You don't need 2 swaps. sda9 is being used, so you CAN remove sda6 if you like, but given it's such a titchy size, you could just leave it alone.

sda7 (which you can't access) is probably a LVM (encrypted) volume. Depending on choices made during installation / creation, you will need a password or a keyfile to access the contents.

If you don't know what it is about, it's probably safe to just reformat just ONLY sda7. You can do this using the Partition Editor (gparted) utility. While you're at it, you can remove sda6 and expand sda7 to take the unpartitioned space of sda6.

Note that any resizing and other partition operations come with an element of risk. It's small, but present. So at your own risk, please.

Unless there is a compelling reason, I would just leave it alone. And, if you are certain that sda7 does not contain any important data, you could try as mentioned above.

btw, I think you are confusing "SATA" with "SSD". Probably both drives are SATA, but the Windows drive is a 32GB SSD.

---

