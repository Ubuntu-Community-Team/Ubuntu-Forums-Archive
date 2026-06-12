---
title: "GRUB error 15, then Error 12"
date: 2007-12-01
forum: General Help
---

### Post by WxGuy1 on 2007-12-01
I've searched long and hard to fix this problem, but none of the solutions I've found online (both here and elsewhere) have worked.  Here's the deal...

I am dual-booting Ubuntu 7.10 and MS Vista Business Edition.  This has worked just fine for weeks (and worked just fine with a previous version of Ubuntu), but when I tried to boot up my computer today, I received a "Loading Grub 1.5... Error 15".  So, I used the Live CD to try to work on GRUB.  I used the GRUB prompt to do the Root, Setup sequence, but I always receive "Error 12: Invalid device requested" in the GRUB prompt.  So, I decide that, just to get a working laptop, I'd try to get the Windows bootloader in the MBR.  Well, I used the rescue CD to do fixboot and fixmbr (technically, "bootrec.exe /fixmbr and bootrec.exe /fixboot"), but now I just get a completely blank/black screen after BIOS does it's thing.  Oy.  So, I'm back to working on getting GRUB in order. 

I then thought about removing the /boot/grub directory entirely and recreate it.  So, here's what I do:

```

root> sudo grub

grub> root (hd0,6)
grub> setup ({TAB}
 Possible partitions are: 
   Partitions num: 0, Filesystem type is fat, partition type 0xc
   Partitions num: 1, Filesystem type unknown, partition type 0x7
   Partitions num: 4, Filesystem type unknown, partition type 0x7
   Partitions num: 5, Filesystem type unknown, partition type 0x82
   Partitions num: 6, Filesystem type ext2fs, partition type 0x83

grub>setup (hd0,6)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/rub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,6)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,6)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,6) /boot/grub/stage2 p /boot/grub/menu.list"... failed

Error 12: Invalid device requested

```

The first time I tried this, I received a similar error (don't think the exact one, but I've since forgotten it). I then rebooted, only to be much with what seemed like an infinite loop of "Starting Grub 1.5..." (i.e. it just kept writing that to the screen, with it requiring me to power off in order to get it to stop).

Here are the contents of my original /boot/grub folder:
default    installed-version    resierfs_stage1_5
device.map jfs_stage1_5   stage1
e2fs_stage1_5  menu.lst  stage2
fat_stage1_5  minix_stage1_5   xfs_stage1_5


Below are some vitals:
```
**sudo fdisk -l**
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000080
    Device    Boot         Start          End          Blocks      Id  System
/dev/sda1   *            19196         19457      2104483+  c W95 FAT32 (LBA)
/dev/sda2               7         3923         31463302+   7  HPFS/NTFS
/dev/sda3               3924     19457    124776855   f  W95 Ext'd (LBA)
/dev/sda5               3924     16926     104445108+  7 HPFS/NTFS
/dev/sda6               19196    19457    2104483+   0  Empty
/dev/sda7               16927    17169    1951866   82 Linux swap / Solaris
/dev/sda8               17170    19195    16273813+  83 Linux

```
My Vista partition is sda2 and my Ubuntu partition is sda8 (which is (hd0,7)).  **_Again, I did nothing between Thursday (when I last booted into Ubuntu) and today_**, but I think Vista may have installed an "important update".  

```
**vim mtab**
/dev/sda8 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mod=620 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```

```
**vim device.map**
(fd0) /dev/fd0
(hd0) /dev/sda
(hd1) /dev/sdb

```

I'll only include the important parts from menu.lst:
```
**vim menu.lst**
# menu.lst - See: grub(8), info grub, update-grub(8)
{CUT}
## ## End Default Options ## ##
title    Windows Vista Business
root   (hd0,1)
savedefault
makeactive
chainloader   +1

title      Ubuntu 7.10, kernel 2.6.22-14-generic
root     (hd0,7)
kernel    /boot/vmlinuz-2.6.22-14-generic root=UUIDC=4547eaae-d3fo-4cdd-99a3-b42b88ddb853 ro quiet splash
initrd     /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root     (hd0,7)
kernel    /boot/vmlinuz-2.6.22-14-generic root=UUIDC=4547eaae-d3fo-4cdd-99a3-b42b88ddb853 ro single
initrd     /boot/initrd.img-2.6.22-14-generic

title    Ubuntu 7.10, memtest86+
root     (hd0,7)
kernel   /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title    Other Operating Systems:
root

title    Microsoft Windows XP Embedded
root   (hd0,5)
savedefault
makeactive
chainloader +1

```

```
**vim partitions**
major minor  #blocks  name
   8    0  156290904 sda
   8    1   2104483   sda1
   8    2   31463302 sda2
   8    3             1  sda3
   8    5   104445108 sda5
   8    6     2104483 sda6
   8    7     1951866 sda7
   8    8     16273813 sda8
   7    0        657224 loop0

```

I'm currently typing this on my wife's laptop, so there may be one or two transcripting errors (I had to retype all of the above, since I didn't feel like going into the other room to hook up my currently-disabled laptop using ethernet cable). I rechecked everything twice, though, so I hope it's error-free.

I've also tried mounting the necessary directories and using grub-install per [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-09167948173503db5923da717a106f0c3aac1cd2](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-09167948173503db5923da717a106f0c3aac1cd2)
, but that doesn't fix anything.

[SIZE="4"]**Any help would be greatly appreciated!**[/SIZE]

---

### Post by WxGuy1 on 2007-12-02
Hmm... I just noticed something.  I want to use sda8, which is also known as (hd0,7).  However, when using the GRUB command prompt, it doesn't show that I can use "Partition num: 7".  This appears as if it could be a problem... I think Partition num: 6 is the Linux SWAP partition. Then again, running "setup (hd0)" after "root (hd0,6)" does still display that /boot/grub/ is found...  Any help?  

To make matters worse, Vista Recovery Console (from the Vista boot disk) no longer sees the Vista partition as a valid partition.  Ugh.

---

### Post by meierfra on 2007-12-02
Can you mount your ubuntu partition from the LifeCD: (or RescueCD)

```

mkdir ubuntu
sudo mount -t ext3 /dev/sda8 ubuntu
```

If this worked, you should  be able to look at your ubuntu files in the folder "ubuntu" and make sure they are o.k. 
> 
dev/sda6               19196    19457    2104483+   0  Empty

Do you know anything about this partition? 


Maybe your partition table got corrupted. Check out TestDisk in my signature.
(testdisk is on the RescueCD)

---

### Post by WxGuy1 on 2007-12-02
Thanks for the help!

The partitions mount just fine using the LiveCD, and everything shows up as expected in fstab and mtab.  I reordered the partitions, so my new "sudo fdisk -l" looks like this:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000080
    Device    Boot         Start          End          Blocks      Id  System
/dev/sda1   *            7         3923         31463302+   7  HPFS/NTFS
/dev/sda2               3924     19457    124776855   f  W95 Ext'd (LBA)
/dev/sda3             19196       19457      2104483+  c W95 FAT32 (LBA)
/dev/sda5               3924     16926     104445108+  7 HPFS/NTFS
/dev/sda6               19196    19457    2104483+   0  Empty
/dev/sda7               16927    17169    1951866   82 Linux swap / Solaris
/dev/sda8               17170    19195    16273813+  83 Linux

```

I set up the partitions several months ago, so I'll try to remember exactly what everything is:
sda1 --> Windows Vista (primary partition)
sda2 --> Extended/logical partition for everything else
sda3 --> [Dell MediaDirect]
sda5 --> Most of my Windows programs, data, and documents 
sda6 --> [Dell MediaDirect]
sda7 --> Linux swap
sda8 --> Ubuntu installation

sda3 and sda6 are the same size and are located on the same part of the hard drive (obviously).  Am I right to be concerned about this?  Does the "Id" tell me anything about this?

I tried using TestDisk, and the partitions show up as above.  However, there is a line that contains the following: "Space conflict between the following two partitions", which precedes sda2 and sda3 (odd, since those two partitions actually don't appear to have a space conflict).  Here's what TestDisk analysis shows:

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition            Start        End    Size in sectors
1 * HPFS - NTFS       6   0   1   3922  254 63  62926605
2 E extended LBA    3923  0 1 19456  254 63 249553710
3 P FAT32 LBA      19195  1 1 19456 254 63    408967 [MEDIADIRECT]
Space conflict between the following two partitions
2 E extended LBA     3923  0 1 19456 254 63 249553710
3 P FAT32 LBA     19195 1 1 19456 254 63  4208967 [MEDIADIRECT]
5 L HPFS - NTFS    3923 1 1 16925 208 46  208890217 [AppsData]
  X extended         19195 0 1 19456 254 63 4209030
  X extended        16926 0 1 17168 254 63 3903795
6 L Linux swap       16926 1 1 17168 254 64 3903795
  X extended       17169 0 1 19194 254 63 32547690
7 L Linux        17169 0 1 19194 254 63 32547690

```

Moving on to the "find partitions created under Windows" (or whatever that prompt is called):
```

   Partition          Start         End     Size in sectors
* FAT16 >32M       0 1 1      5 254 63    96327 [DellUtility]
P HPFS - NTFS      6 0 1 3922 254 63   6296605
L HPFS - NTFS  3923 1 1 16925 254 63 208893132 [AppsData]
L Linux Swap     16926 1 1 17168 254 63    3903732
L Linux         17169 1 1 19194 254 63   32547627
L FAT32 LBA     19195 1 1 19456 254 63    4208967 [MEDIADIRECT]

```

---

### Post by WxGuy1 on 2007-12-02
Well, I'm making more progress. I've putzed around with the Vista installation disk several more times, and I can now boot into Vista just fine.  In Vista, Disk Management utility shows all the partitions correctly.  So, I figure that I'll just reinstall Ubuntu 7.10 in it's non-working partition in an attempt to rectify the GRUB situation.  Before that, though, I tried the GParted liveCD, but it showed the entire drive as unallocated space (no partitions). So, I load up the Ubunu LiveCD and try to reinstall Ubuntu.  Well, the Ubuntu installation process is also telling me that the entire hard drive is unallocated. UGH!  So, get this:

+ Vista sees the partitions just fine, and it can read the contents just fine
+ The partitions show up when I boot into the LiveCD and use "sudo fdisk -l".
+ The partitions show up just fine when I use TestDrive
+ I can mount the partitions when I boot using the LiveCD (sudo mount /mnt/Vistadrive /mnt/sda1, for example), and all the contents of the mounted partitions are readable
**BUT**
- The partitions do NOT show up in GParted, nor do they show up when I try to reinstall Ubuntu (though the Ubuntu install process may use GParted I suppose)

Any ideas?  I can't reinstall GRUB for all the reasons listed in previous posts in this thread.  So, as it is now, I cannot boot into Ubuntu...

---

### Post by meierfra on 2007-12-02
It looks like that only the partition table is screwed. How much did you play around with testdisk?. Did your ever select "search" to do a deeper search? Did you ever click on "write" to rewrite the partition table?


> "find partitions created under Windows"

Sorry, none of my partitions have  been created by Windows. So I have never seen this prompt.

---

### Post by teryowen on 2007-12-02
have u tried installing GRUB, by booting of a live CD and installing the grub like so:

sudo grub
root (hd0,7)
setup (hd0)
quit

this will stop you from booting into Vista, but if you have the entry for vista in grub then it is going to be able to go into vista

EDIT: didn't see that you couldn't...

As for you partition table stuff, be very carefully because if its faulty the partition table that is then you risk losing your data, happened to a friend of mine.

EDIT 2: I looked more carefully over your stuff you were trying to install GRUB on the hd0,6 which is the 7th parition but thats swap, so try instead hd0,7 for the 8th partition where ubuntu is

---

### Post by WxGuy1 on 2007-12-02
> **teryowen said:**
> have u tried installing GRUB, by booting of a live CD and installing the grub like so:

sudo grub
root (hd0,7)
setup (hd0)
quit

....

EDIT 2: I looked more carefully over your stuff you were trying to install GRUB on the hd0,6 which is the 7th parition but thats swap, so try instead hd0,7 for the 8th partition where ubuntu is

Yeah, when I try root (hd0,7), I receive the following error:

```

grub> root (hd0,[tab]
Possible partitions are:
 Partitions num: 0, Filesystem type unknown, partition type 0x7
 Partitions num: 2, Filesystem type is fat, partition type 0xc
 Partitions num: 4, Filesystem type unknown, partition type 0x7
 Partitions num: 5, Filesystem type unknown, partition type 0x82
 Partitions num: 6, Filesystem type is ext2fs, partition type 0x83

grub> root (hd0,7)
Error 22: No such partition

```

After a GIS for grub partition type, it appears that "partition type 0x82" is given for SWAP and "partition type 0x83" is a standard EXT3/EXT2 partition.  If that's the case, then it looks like the partition num 5 and 6 are SWAP and my current/previous Ubuntu installation partition (which should be mounted as root, or / ), respectively.  This, however, is at odds with what fdisk shows... If I choose "root (hd0,6)", then "setup (hd0)", I get the errors received above (namely, "Error 12: Invalid device requested").  :confused:

---

### Post by WxGuy1 on 2007-12-02
> **meierfra said:**
> It looks like that only the partition table is screwed. How much did you play around with testdisk?. Did your ever select "search" to do a deeper search? Did you ever click on "write" to rewrite the partition table?


I played around with TestDisk a bit, and I did both "deeper search" and "write".  This, however, was after about 10 hours of troubleshooting yesterday, so it didn't cause the initial errors.  In fact, it wasn't until after I did this in TestDisk that I could even get the Windows Recovery Console to repair the MBR enough to boot into Vista.

I agree that it's likely a partition table problem.  The question is -- why do Vista and fdisk see the partitions just fine (and why can I mount them just fine) but GParted and the UBuntu installation process cannot see them?

In the  vein, this particular problem appears similar to the problem listed here --> [http://ubuntuforums.org/showthread.php?t=415274](http://ubuntuforums.org/showthread.php?t=415274) . Alas, no solution is given in that thread, other than to use TestDrive.

---

### Post by meierfra on 2007-12-02
I heard once that different partitioning programs use slightly different  conventions on how to write a partition table. So your troubles  could be a conflict  between the Vista Partitioner and Gparted. But I really don't know.

After testdisk wrote the partition table,  do you still have  "Dell  Media Direct" listed twice?

---

### Post by WxGuy1 on 2007-12-02
> **meierfra said:**
> 

After testdisk wrote the partition table,  do you still have  "Dell  Media Direct" listed twice?

Thanks for your help, Meierfra!

My current "Analysis" from TestDisk is the same as given above:
```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition            Start        End    Size in sectors
1 * HPFS - NTFS       6   0   1   3922  254 63  62926605
2 E extended LBA    3923  0 1 19456  254 63 249553710
3 P FAT32 LBA      19195  1 1 19456 254 63    408967 [MEDIADIRECT]
Space conflict between the following two partitions
2 E extended LBA     3923  0 1 19456 254 63 249553710
3 P FAT32 LBA     19195 1 1 19456 254 63  4208967 [MEDIADIRECT]
5 L HPFS - NTFS    3923 1 1 16925 208 46  208890217 [AppsData]
  X extended         19195 0 1 19456 254 63 4209030
  X extended        16926 0 1 17168 254 63 3903795
6 L Linux swap       16926 1 1 17168 254 64 3903795
  X extended       17169 0 1 19194 254 63 32547690
7 L Linux        17169 0 1 19194 254 63 32547690
```

---

### Post by meierfra on 2007-12-02
Your Dell Media Partition is  marked as a Primary partion and  but sits inside your extended partition. 

There are two possibilities: 

1) Dell Media is supposed to be a primary partition and but   the end point of  the extend partition is marked wrong

2) Dell Media is really a logical partition.

I vote for 2).  Use testdisk to mark the media partition as a logical partition and "write" a new partition table.

---

### Post by WxGuy1 on 2007-12-02
> **meierfra said:**
> Your Dell Media Partition is  marked as a Primary partion and  but sits inside your extended partition. 

There are two possibilities: 

1) Dell Media is supposed to be a primary partition and but   the end point of  the extend partition is marked wrong

2) Dell Media is really a logical partition.

I vote for 2).  Use testdisk to mark the media partition as a logical partition and "write" a new partition table.

The Dell MediaDirect 3 partition should be, if I've read on other sites correctly, a logical partition.  It is designed such that it will be booted if the "MediaDirect" button is pressed when the computer is powered off.  FWIW, the MediaDirect button is right next to the Power button on my laptop (Dell Inspiron 6400), and it's designed to allow users to play music and video without booting into a full Windows installation.   I just noticed, in trying to boot directly into MediaDirect, though, that when the "Dell MediaDirect" boot screen comes up immediately after the BIOS loads, I get "GRUB loading stage 1.5" on the top of the screen (above the Dell graphic), and then the boot hangs.  So, it looks like grub is trying to run on the MediaDirect partition.  I'm going to try to reinstall MediaDirect (if it doesn't require me to repartition), then I'll try you suggestion given above. Again, thanks!

UGH: After trying to boot into MediaDirect, I tried to boot back into Vista... I'm getting nothing but "GRUB loading stage 1.5" line after line (like it keeps trying to repeat itself).  I can no longer boot into Vista.  How did GRUB reinsert itself into the MBR if I didn't do anything related to the MBR between now and the last time I booted into Vista like 10 minutes ago?

---

### Post by WxGuy1 on 2007-12-03
Well, I think I can close out this thread.  In case others have similar problems, though, I'll give my solution...

1.  Basically, I used the Vista installation disk to do the following "bootrec.exe /fixmbr" and "bootrec.exe /fixboot".  This allowed me at least to boot into Vista, though I sometimes had to do the above more than once to get everything working. 
2.   When I got into Vista, I installed the following free-ware package --> EasyBCD 1.7.1, which can be downloaded at [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1) .  This let me rewrite the MBR to put in an entry for my Linux installation using the Microsoft Vista bootloader.  
3.  After saving and rebooting, the Windows Vista bootloader brought up the option of either booting into Vista or booting into whatever /boot/grub dictated on my Linux partition; I used EasyBCD to add an entry for my L drive (which was mapped from /dev/sda8).  At any rate, selecting the newly-added option in the Vista bootloader menu, menu.lst given in /dev/sda8/boot/grub was called up.  
4. I selected the line "Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)" and logged is as root. 
5. A quick "fdisk -l" showed the partitions just fine, so I got into the grub prompt (by typing "grub" at the prompt), then did "root (hd0,7)" followed by "setup (hd0)".  SUCCESS!   I didn't receive the "Error 12: Invalid device requested" that I received every other time that I ran the two above commands.    
6.  I rebooted from recovery mode, and, voila!, GRUB pops up and gives me the correct options given in menu.lst .  All entries work from this menu!  If I choose Vista (/dev/sda2), then it brings up the Vista bootloader menu, from which I can choose "Vista" again to boot into that Windows. FWIW, if I choose "Linux" from the Vista bootloader menu, I'm brought back to the GRUB loader.

Now, I haven't yet checked to see if GParted can read the partitions correctly, but at least it's up and working. It's worth noting that you can go back into Vista and run EasyBCD again to remove the Linux entry added to the Windows Vista bootloader.  Since I only added one entry originally, the deletion of this entry left only 1 entry in the Vista bootloader list, which means that Vista now boots correctly (i.e. the Vista bootloader list doesn't come up when I select my Vista partition / sda8 from the grub menu).

---

### Post by Drone4four on 2008-04-25
Me and a few others are tackling a very similar problem in this thread: 
[http://ubuntuforums.org/showthread.php?p=4790067&posted=1#post4790067](http://ubuntuforums.org/showthread.php?p=4790067&posted=1#post4790067)
I talk WxGuy1's thread  a lot. =D

---

