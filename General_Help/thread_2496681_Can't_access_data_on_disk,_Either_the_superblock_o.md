---
title: "Can't access data on disk, Either the superblock or the partition table is likely to"
date: 2024-04-08
forum: General Help
---

### Post by cef24 on 2024-04-08
[LIST]
[*]I was running out of space in /home, so I fired up gparted to shrink /root (on the left side of /home on the physical drive), 
[*]moved the allocated space up to the right of home, expand. 
[*]I clicked the tick icon to proceed to operations, but somehow when coming back I was left with /root shrinked to 40G (ok),
[LIST]
[*]but : unallocated 60G on left side of /home, and unallocated 1.86 MiB on right side of /home (which I believe weren't there beforehand, not sure tho 
[/LIST]
  
[*]I used a kubuntu20 live stick to do, but I'm not sure as my daily driver uses KDE too, so now I start wondering if I didn't do all that while having booted on the daily driver OS itself... But I guess no, as gparted wouldn't have let me do stuff on disk that is mounted. 
[/LIST]

After that I couldn't boot on the OS anymore, I do still have the grub screen with ubuntu and windows choice, but when proceeding to default (ubuntu) I land on a black console screen. I can still boot on windows, it hasn't been damaged as the partitions sit on the left of /root.

I used clonezilla and dd CLI to clone the corrupted drive (500G) on other drives (1TB and 2TB), and I'm trying to recover stuff on the other drives, to be safe.

I pulled out all the disks from the laptop, and have only the gparted live stick plugged (15GB), with an USB SSD enclosure of the corrupted drive clone.

[IMG]https://ibb.co/jLktbNW[/IMG]

[IMG]https://ibb.co/Yt9xRvx[/IMG]


[LIST]
[*]The failed partition, which was /home , is /dev/sdd8, 
[*]there's an exclamation sign icon on gparted GUI on its line (there isn't any home flag on the gparted GUI line now tho), 
[*]rightclicking info, I get :
[LIST]
[*]file system : ext4, size 99.50 GiB , UUID 788801ddd-... 
[*]First sector : 729034752 , last sector : 937699327 , total sectors : 208664576 
[*]"Warning :
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support: e2fsprogs v1.41+" 
[/LIST]
  
[*](I googled already this and it's not the cause of the issue, gparted live is latest, version gparted-live-1.6.0-1-amd64 
[/LIST]

$ cd ~ && mkdir /temp
$ sudo mount /dev/sdc8 ~/temp
mount: /home/user/temp: wrong fstype, bad option, bad superblock on /dev/sdc8, missing codepage or helper program, or other error. dmesg(1) may have more information after failed mount system call.

$ sudo fsck.ext4 -v /dev/sdc8
e2fsck 1.47.0 (5-Feb-2023)
The filesystem size (according to the superblock) is 26083327 blocks
The physical size of the device is 26083072 blocks
Either the superblock or the partition table is likely to be corrupt !
Abort<y>? yes
[LIST]
[*](same answer with $ sudo e2fsck -f /dev/sdc8 ) 
[*]I made the hand calculus, the difference = 255 blocks. *4096 bytes = 1 044 480 bytes = 0.9960938 mib
so this doesn't explain the 1.86 MiB on right side. Maybe the blocks equal 2*4096 bytes ? But this would lead to 255*2*4096 = 1.992188 MiB
exceeding 1.86... 
[/LIST]

$ sudo ddrescue /dev/sdc8 /mnt/tmp/home_backup.img
[LIST]
[*]used losetup to then mount he .img on /loop1 
[/LIST]
$ sudo e2fsck -b 32768 /dev/loop1
The filesystem size according to the superblock is 26083327
The physical size of the device is 26083072 blocks
Either the superblock or the partition table is likely to be corrupt !
Abort<y>? yes
/dev/loop1: **** FILE SYSTEM WAS MODIFIED ******

$ sudo dumpe2fs /dev/loop1 | grep "Block size"
dump2fs 1.47.0
Block size : 4096
dumpe2fs: Block bitmap checksum does not match bitmap while trying to read '/dev/loop1' bitmaps
$ sudo mkfs.ext4 -b 4096 -S /dev/loop1
/dev/loop1 contains a ext4 file system
last mounted on /home on Tue Mar 26 03:11:39 2024
Proceed anyway? y
Discarding device blocks: done
Creating fiesystem with 26083072 4k blocks and 6520832 inodes
Filesystem UUID : d5315...
Superblock backups stored on blocks : 32768 ,..., 23887872
Allocating group tables: done
/dev/loop1 may be further corrupted by superblock rewrite
Proceed anyway ? y
Skipping journal creation in super-only mode
Writing superblocks and filesystem accounting information: done

$ sudo e2fsck -B 4096 -f -y -v /dev/loop1
...
Creating journal (131072 blocks): DOne.
*** journal has been regenerated ***
/dev/loop1: *** FILE SYSTEM WAS MODIFIED ***
11 inodes used (0.00%, out of 6520832)
0 non-contiguous files
0 bad blocks
0 regular files
1 link
$ sudo mount /dev/loop1 /mnt/tmp
$ ls /mnt/tmp
lost+found

**Is there a way to get this partition working again ? Is there a way to just mount somehow the partition for me to copy paste important files on a USB stick ?**

I'm really desperate as I'm kinda the brain/manager guy for the whole fam and 5 years worth of notes were in that /home partition

---

### Post by yancek on 2024-04-08
Posting the output of the command:  sudo fdisk -l would be more useful as it shows sectors for each partition.  What you describe in the first two sentences of your post doesn't really make sense.  Are you trying to move the filesystem partition to the left to gain space for the /home partition which is to the right of the filesystem partition?  /root is the /home directory of the root user and there would be no reason for it to be on a separate partition.  If you have 60GB of free space now between the / filesystem partition and the /home partition, you will need to use a 'live' cd with gparted or similar software to move the /home to the left where you have unallocated space.  This will require moving all the data on that partition to the left which will take some time.  If you post the fdisk output, someone should be able to give you more detialed advice and possibly another method to use.  You should not try to modify mounted partitions so using a 'live' Linux would be the way to go.

You can only expand a partition to contiguous space on the drive.  You could have shrunk the / partition and created another data partition but without sector information from fdisk, we're just guessing.

---

### Post by cef24 on 2024-04-08
Sorry I attached a screenshot imgur/ibb link to the initial post but it didn't seem to work, thank you very much for replying, here is the output :

$ sudo fdisk -l
Disk /dev/sdb: 14.32 GiB, 15376318464 bytes, 30031872 sectors
Disk model: Ultra
Units: sectors of 1 * 512 = 512 bytes
Disklabel type: dos
Disk identifier: 0x01ecfe01

Device       Boot       Start                End        Sectors      Size      Id      Type
/dev/sdb1                     64       1073151      1073088     524M    17     Hidden HPFS/NTFS
/dev/sdb2   *       1073152      30029823    28956672   13.8G     c       W95 FAT32 (LBA)

Disk /dev/loop0: 460.37 MiB, 482734080 bytes, 942840 sectors
Units: sectors of 512 bytes
[B]The backup GPT table is not on the end of the device.

[/B]Disk /dev/sdc (not relevant, just there to try to put testdisk findings on it if any)

Disk /dev/sdd: 1.82 TiB (this is a clone of the original 500GB corrupted disk, used clonezilla to clone the most part, then dd on corrupted partition as it was flagged with exclamation sign on gparted GUI, after using dd it was appearing without the sign, as when I plugged the og 500GB disk and looked at it with gparted GUI)
2000398934016 bytes, 3907029169 sectors
Disk model: PCIe
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
IO size (minimum/optimal): 4096/4096 bytes
Disklabel type : gpt
Disk identifier: 44EB1DBE-...

Device              Start           End       Sectors      Size    Type
/dev/sdd1         2048      534527       532480    260M   EFI System
/dev/sdd2      534528      567295        32768      16M  Microsoft reserved
/dev/sdd3      567296 438628351 438061056 208.9G  Microsoft basic data
/dev/sdd4 438628352 440676351    2048000
/dev/sdd5 440676352 **441724926**    1048575    512M  EFI System 
/dev/sdd6 **441724928** 523644927   81920000  39.1G  Linux filesystem
/dev/sdd7 523644928 **601237503**   77592576     37G  swap
/dev/sdd8 **729034752** 937699327 208664576  99.5G   Linux filesystem

(me : currently there are ~60G unallocated space between sdd7 and sdd8 on the gparted GUI view)

edit : I also just tried $ testdisk
did quicksearch and deeper search
at the end it highlights EFI System, Linux Swap, and Linux filesys. data (associated to previous /home) in color green
but when hitting "p" to list file I only have 4 lines

edit2 : also I found a picture of the gparted display right BEFORE the accident happened, / was weighing 100.00 GiB with 26.18 GiB used, /home was 99.50 GiB with 91.55 GiB used

edit3 : I used this tutorial [https://linuxconfig.org/how-to-recover-partition-table-in-linux](https://linuxconfig.org/how-to-recover-partition-table-in-linux) on the full disk clone I had of the original drive. Choosing the "write option" for the 8th partition, it basically deleted every single partition of it, keeping only sdc1 EFI, swap becoming sdc2, and /home becoming sdc3. I rebooted on the live gparted usb, plugged the newly changed clone disk,
$ mkdir test/ && sudo mount /dev/sdc3 ~/test/
$ sudo ls test/
lost+found   me
(me was indeed my username) So I right clicked on desktop, opened filebrowser, but clicking only once on the "me" file, I get info on the bottom left and right of the file browser : on the left it says "me" inode/x-corrupted type, and on the right it says "Free space 2.9 GiB (Total:97.9 GiB). Contrary to the lost+found icon which is a folder, the me file has a textfile icon.
$ sudo ls test/me/
ls: cannot access 'test/me': Bad message

Am I missing on something?

---

### Post by cef244 on 2024-04-22
I forgot which email I've used to sign up. Just to inform whoever that I moved this thread to [https://bbs.archlinux.org/viewtopic.php?pid=2166439#p2166439](https://bbs.archlinux.org/viewtopic.php?pid=2166439#p2166439)

---

### Post by yancek on 2024-04-23
In your initial post, you indicate that sdd8 was your /home partition and that you were running out of space on it and wanted to enlarge it so you wanted to shrink /root to the left.  You mean the / (root) filesystem partitio sdd6?  Your fdisk output shows a swap partition between /home and the / filesystem partition.  If you wanted to move /home to the left, you could have deleted the swap which shows as 37GB which is excessive.  Recent Ubuntu's create a swap file so a swap partition would not have been necessary but still could have been used.  Another thing I noticed which is unrelated is that you have 2 EFI partitions on the drive when only one is needed.

If you had deleted swap then moved /home (sdd8) to the left that should have worked.  This would have meant moving data on the partition also so would have taken some time.  You could have left some space at the end of the new /home for a new swap partition if you wanted.

If you look at the end sector for sdd8 and compare it to the total sectors for the drive, it looks like you have room to the right of sdd8 to expand?

---

