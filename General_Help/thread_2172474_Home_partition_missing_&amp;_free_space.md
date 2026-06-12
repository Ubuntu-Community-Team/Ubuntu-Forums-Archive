---
title: "Home partition missing &amp; free space"
date: 2013-09-05
forum: General Help
---

### Post by ibrahimrasheed52 on 2013-09-05
So I was using Windows 8 and for my work purpose I had to install Windows 7 back by simply deleting the 200MB partition and 100GB partition of windows and I was able to install windows 7 successfully. Then because I have UBUNTU as dual boot I did used the BOOT-REPAIR through live cd and repaired my GRUB2 but since then my HOME partition is missing and it is showing as FREE SPACE in both WINDOWS 7 (computer management) and DISK MANAGEMENT of UBUNTU live CD. 

I am really scared and I got tonnes of important emails and data which I can lose and I just thought of giving a try by SYMANTEC PARTITION MANAGER but it says ERROR 105 so I didn't do anything. What I should do now ?

---

### Post by ibrahimrasheed52 on 2013-09-05
Please help anyone :(

---

### Post by Bashing-om on 2013-09-05
ibrahimrasheed52;
Let's see what the disk(s) partitioning is for starters. See what there is to work with/from.
Boot up the liveDVD -try ubuntu mode- from the desktop key combo ctl+alt+t yields a terminal;
Post back the output of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```

[INDENT][INDENT]a tale is told
[/INDENT][/INDENT]

---

### Post by ibrahimrasheed52 on 2013-09-05
sudo fdisk -lu
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xef3e837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   210146264   104969708+   7  HPFS/NTFS/exFAT
/dev/sda3       210130944   270131199    30000128   83  Linux
/dev/sda4       270133246   976773167   353319961    f  W95 Ext'd (LBA)
/dev/sda5       830962128   935811071    52424472    7  HPFS/NTFS/exFAT
/dev/sda6       935811136   976773167    20481016    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 7885 MB, 7885291520 bytes
255 heads, 63 sectors/track, 958 cylinders, total 15400960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c354660

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *         128    15400959     7700416    c  W95 FAT32 (LBA)

```

sudo parted -l
```
Error: Can't have overlapping partitions. 

```


sudo parted /dev/sda unit s print


```

sudo parted /dev/sda unit s print
```

lsblk -f

```
NAME   FSTYPE LABEL MOUNTPOINT
sda                 
&#9500;&#9472;sda1              
&#9500;&#9472;sda2              
&#9500;&#9472;sda3              /media/ubuntu/1c608166-958a-4bac-ae2a-63503f64a1d9
&#9500;&#9472;sda4              
&#9500;&#9472;sda5              /media/ubuntu/LENOVO
&#9492;&#9472;sda6              /media/ubuntu/LENOVO_PART
sdc                 
&#9492;&#9472;sdc1              /cdrom
sr0                 
loop0               /rofs


```

---

### Post by Bashing-om on 2013-09-05
ibrahimrasheed52; My error !

Windows 8 uses GPT partitioning .. and the tool "fdisk" is an inappropriate application. (fdisk is for the older MBR partitioning tables).

I do not know if the tool "gdisk" is installed by default. We will need "gdisk" to examine your drive.
let's see:
```

dpkg -l gdisk

```

presently as an aside... I see there is an "extended" partition ... As GPT partitioning is dynamic, why would an "extended" partition even exist ?
Let's see what "gdisk" relates.

[INDENT][INDENT]to err is human, to really mess up is sometimes me
[/INDENT][/INDENT]

---

### Post by ibrahimrasheed52 on 2013-09-05
dpkg-query: no packages found matching gdisk

---

### Post by ibrahimrasheed52 on 2013-09-05
One more thing which i discovered during /etc/fstab in gedit is the following.

overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by Bashing-om on 2013-09-05
ibrahimrasheed52; Then 

We need to get it ..from the liveDVD ->try ubunru mode -> terminal;
```

sudo apt-get install gdisk

```
will not persist after reboot
then after installed ... do in terminal:
```

sudo gdisk -l

```
and will see what we are looking at.

[INDENT][INDENT]2 steps forward and one back
[/INDENT][/INDENT]

---

### Post by ibrahimrasheed52 on 2013-09-05
I enabled the Universal option in SOFTWARE SOURCES so was able to download.

```
root@ubuntu:~# sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format.
***************************************************************


Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sda: 976773168 sectors, 465.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7CFC725E-3A73-4C19-838A-38D11270C82B
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 976773134
Partitions will be aligned on 16-sector boundaries
Total free space is 560833006 sectors (267.4 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   0700  Microsoft basic data
   2          206848       210146264   100.1 GiB   0700  Microsoft basic data
   3       210130944       270131199   28.6 GiB    8300  Linux filesystem
   5       830962128       935811071   50.0 GiB    0700  Microsoft basic data
   6       935811136       976773167   19.5 GiB    0700  Microsoft basic data


```

---

### Post by ibrahimrasheed52 on 2013-09-05
[B]Total free space is 560833006 sectors (267.4 GiB)

This is my HOME partition space which is showing as FREE SPACE.
[/B]

---

### Post by Bashing-om on 2013-09-05
ibrahimrasheed52;

I agree the results seem frightening. 
1. I am willing to try and help but
a) I have no experience with UEFI (Windows' can of worms)
b) Windows no longer exist in my world, I left Windows behind a long time ago and have no need to look back.

2. oldfred, a forum moderator, is the recognized authority on UEFI. It will be beneficial for you to search this forum .. using the tags "oldfred" for the username and "uefi" for the term.

3. I am aware of several procedures ... but my lack of experience may hamper things. ->

4. To me it looks as if the partitioning was initially as GPT and ubuntu should have been installed in "UEFI" mode to correspond to that of Windows' partition scheme. Instead /// MBR has been introduced...which is going to upset windows. -> Windows' fix disk utility to repair ?? and then

5. Once Windows is fully operational in UEFI mode ... (re-)install ubuntu making sure it also is in UEFI (????) 

With that said ... here is what is:
Did you have initially a separate /home partition ?... 

sda3 is a linux partition and we can look at it and see what is there ..
from the liveDVD terminal codes:
```

sudo mkdir /mnt/looking
sudo mount /dev/sda3 /mnt/looking
ls -la /mnt/looking/

```
will give us a broad spectrum looksee and one can drill about once the names of the directories are known.
When done looking ... must(!!!) manually (un-)mount that sda3 filesystem ...
```

sudo umount /mnt/looking

```

I am willing to help, in any way I can; be aware ->
[INDENT][INDENT]I am not the sharpest tool in this tool box[/INDENT][/INDENT]

---

### Post by ibrahimrasheed52 on 2013-09-06
Yes I have a separate HOME partition besides the ROOT partition. Ill have a look at it in few minutes and post the results. Thanks.

---

### Post by ibrahimrasheed52 on 2013-09-06
I am sure you must have noticed that in this list of output through "blkid" command I am missing a partition sda4 which seems to be HOME PARTITION

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="System Reserved" UUID="74AA" TYPE="ntfs" 
/dev/sda2: UUID="A4246" TYPE="ntfs" 
/dev/sda3: UUID="1c6-958a-4-ae2a-6350" TYPE="ext4" 
/dev/sda5: LABEL="LENOVO" UUID="84BA6B2EB" TYPE="ntfs" 
/dev/sda6: LABEL="LENOVO_PART" UUID="720E8F TYPE="ntfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="0903-E" TYPE="vfat"

(modified the actual UUIDs while posting)

---

### Post by ibrahimrasheed52 on 2013-09-06
It is just the ROOT partition I found through the commands you posted.

---

### Post by ibrahimrasheed52 on 2013-09-06
As I had mentioned earlier that Sda4 is missing and it seems to be my lost HOME partition. So when I do "sudo mount /dev/sda4 /mnt/looking" I get this error. 

mount: you must specify the filesystem type


By the way I did testdisk and found my ibrahim52 but I don't want to go further in it as I want to restore that partition in previous state instead of data recovery or whatver you suggest.

---

### Post by Bashing-om on 2013-09-06
ibrahimrasheed52;

I do not foresee a method to recover the former /home partition, but we can at least look and see about the possibility.
I can not explain why the MBR utility "fdisk" sees a partition sda4, while the GPT utility "gdisk" does not see it.
Let's look about:
From the liveDVD activate GParted (search term in dash) .. and post back the screenshot of what GParted sees for the sda hard drive; as well post back the results of terminal codes:
```

sudo parted -l
sudo parted /dev/sda unit s print

```
still looking for the Windows boot sector's UEFI.

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by westie457 on 2013-09-06
This could well be the problem.> [COLOR=#000000][FONT=Ubuntu Mono]/dev/sda2          206848   210146264   104969708+   7  HPFS/NTFS/exFAT[/FONT][/COLOR]

As reported in the Boot info script sda2 overlaps into sda3.

You could shrink sda2 by a small amount (around 30 MiB should be enough) to make the lost partition visible again.

Ideally the adjustment should be made from inside Windows MMC. It can be done using Gparted however Windows will probably want to run a 'chkdsk' at the nxt boot into Windows.

A few weeks back I had a HDD that Gparted showed as RAW (unformatted) and 'Disks' showed it as fully partitioned and working. In this case the Swap partition had got corrupted and resized from 2GB to about 1.8 TB. Far to big to fit on a 500GB drive. A bit of juggling brought the drive and information back to life.

Hope this helps.

---

### Post by Bashing-om on 2013-09-06
@ westie457 Great catch .. as I live and learn !

[INDENT][INDENT]no step that for a stepper
[/INDENT][/INDENT]

---

### Post by ibrahimrasheed52 on 2013-09-07
Well I have deleted the entire partition, it was of Lenovo Recovery partition and I don't need it. So let me check and ill let you know.

---

### Post by ibrahimrasheed52 on 2013-09-07
> **Bashing-om said:**
> ibrahimrasheed52;

I do not foresee a method to recover the former /home partition, but we can at least look and see about the possibility.
I can not explain why the MBR utility "fdisk" sees a partition sda4, while the GPT utility "gdisk" does not see it.
Let's look about:
From the liveDVD activate GParted (search term in dash) .. and post back the screenshot of what GParted sees for the sda hard drive; as well post back the results of terminal codes:
```

sudo parted -l
sudo parted /dev/sda unit s print

```
still looking for the Windows boot sector's UEFI.
[INDENT][INDENT]all we can do is try
[/INDENT]
[/INDENT]



For both the commands its just the same output results.

Error: Can't have overlapping partitions.

---

### Post by Bashing-om on 2013-09-07
ibrahimrasheed52; Not looking good for the home team;

Show:
```

sudo fdisk -lu

```and let's see what the current partitioning alotment is.
Maybe we can move a partition ? -> NOT a good thing to do, if there is to be an attempt to recover data (/home). Any write or movement on that disk will hamper recovery procedures.

[INDENT][INDENT]cloudy and overcast in doubt
[/INDENT][/INDENT]

---

### Post by westie457 on 2013-09-08
@ibrahimrasheed52
Please do not make the task of recovering the lost partition harder than it already is. Any actions from you like the one quoted will add to the difficulty.> [COLOR=#000000]Well I have deleted the entire partition, it was of Lenovo Recovery partition and I don't need it. So let me check and ill let you know.[/COLOR]

Now back to the issue. Partition SDA2 has been created and written over the PBR (partition boot record) of SDA3 and needs to be made smaller to bring SDA3 back to life.

In my earlier post I suggested to you to shrink SDA2 by a small amount. Now I am going to suggest that you now boot into Windows and go into the MMC. Windows start button > right-click Computer > Manage. In this window select 'Disk management'. You will find it in the left pane under 'Storage.
Now select the main Windows partition (C:) right-click and shrink. Accept the default values that Windows will allow you to shrink the drive. Click 'Yes/OK to all questions that appear. Wait until this has finished.

Reboot into the LiveCD\USB and post the outputs that Bashing-om has asked for and for good measure post a screenshot of Gparted.
Hopefully we will see SDA3 as a usable partition with your files in it. If that happens you can at least copy them to an external drive for safe-keeping.

Whether the files magically reappear or not the next stage in this repair process will need Testdisk. The advice for that will come after you have done the above.

Do not do anything to the free space created when Windows has been resized. It is important to leave the free space for now.

---

### Post by ibrahimrasheed52 on 2013-09-10
> **westie457 said:**
> @ibrahimrasheed52
Please do not make the task of recovering the lost partition harder than it already is. Any actions from you like the one quoted will add to the difficulty.

Now back to the issue. Partition SDA2 has been created and written over the PBR (partition boot record) of SDA3 and needs to be made smaller to bring SDA3 back to life.

In my earlier post I suggested to you to shrink SDA2 by a small amount. Now I am going to suggest that you now boot into Windows and go into the MMC. Windows start button > right-click Computer > Manage. In this window select 'Disk management'. You will find it in the left pane under 'Storage.
Now select the main Windows partition (C:) right-click and shrink. Accept the default values that Windows will allow you to shrink the drive. Click 'Yes/OK to all questions that appear. Wait until this has finished.

Reboot into the LiveCD\USB and post the outputs that Bashing-om has asked for and for good measure post a screenshot of Gparted.
Hopefully we will see SDA3 as a usable partition with your files in it. If that happens you can at least copy them to an external drive for safe-keeping.

Whether the files magically reappear or not the next stage in this repair process will need Testdisk. The advice for that will come after you have done the above.

Do not do anything to the free space created when Windows has been resized. It is important to leave the free space for now.

THANK YOU VERY MUCH GUYS for all your suggestions and advices but unfortunately I didn't had much time to experiment and all my emails were so important that finally I had to remove all the linux partitions through DISK MANAGEMENT of windows and than reinstall Ubuntu. This is what I did.

1. I recovered my home partition through testdisk (Wonderful tool)
2. I tried to install ubuntu 13.04 again but still even after deleting the LENOVO_PART (Windows OS recovery) partition. The whole Disk was showing as UNALLOCATED by Gparted or DISK program of Ubuntu LIVE.
3. I then removed all the UBUNTU partitions through windows DISK MANAGEMENT (mmc) and finally when I booted with live cd of Ubuntu I could rebuild the partitions successfully.

I am so so sorry that I wasted your times Gentlemen. I didn't mean to but I was also helpless because I didn't had much time to experiment getting my HOME partition back. What I really learnt out of this is that never install WINDOWS 8 along with UBUNTU. I am so sorry.

---

### Post by Bashing-om on 2013-09-10
ibrahimrasheed52; Hey .

Not a problem at all .. glad ya got things sorted out.
The situation with Windows is that one has to install Windows 1st, and is generally advised to use Windows tools to set aside the unallocated space in which to install ubuntu <- just for future reference.

[INDENT][INDENT]open source, we are all in this together
[/INDENT][/INDENT]

---

