---
title: "Multiple issues with Ubuntu 13.10 re-install(This should help everyone)"
date: 2014-02-17
forum: General Help
---

### Post by Kemper_Jacobs on 2014-02-17
Hi, thanks in advance for your help.

I have been diving deep into Linux the last couple of months and it has def been an experience. I have learned a ton just from troubleshooting. My problem is that I was trying to fix the wireless driver problem with 13.10 and ended up with a kernel panic. I have even changed the HD with another one and can't seem to fix all the issues. I am getting an error 5 when trying to re-install from LiveCD and getting a completely different error when I was trying to revert back to the working Windows 8 that was on this new hard drive. I have spent the last three days on great forums like this trying to get to a point where my labtop functions again. Ideally, at this point, I wish I could just wipe everything and start over with a fresh install but it seems there is always another issues every time I change directions when trying to fix this issue. 

Ask any questions and I will immediately try to give feedback to try to help fix the problem. 

I have an Acer 5750-9292. 
I am trying to install Ubuntu 13.10 amd64(had it on here before but in the grub menu, command "set" shows i386).... Did I change this on accident?

I can get to the terminal in the live boot with no problem but have no idea what I should do next because I get the "error 5" issue when I try to actually install.

I have been gathering info from my trials and it seems to be an issue with the partitions. 


Is there a way to completely wipe the drive and re-install fresh to get around these issues?

---

### Post by deadflowr on 2014-02-17
Is what is here the kind of error you are getting
[http://askubuntu.com/questions/65830/errno-5-input-output-error-when-trying-to-install](http://askubuntu.com/questions/65830/errno-5-input-output-error-when-trying-to-install)

And helpfully the fix to set it straight.

---

### Post by Kemper_Jacobs on 2014-02-17
here is what RESULTS.txt says

```
             Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048       499,711       497,664  83 Linux
/dev/sda2             501,758 1,250,263,039 1,249,761,282   5 Extended
/dev/sda5             501,760 1,250,263,039 1,249,761,280  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3372a35d-7ae8-4be2-b98e-6dfeba51297a   ext2       
/dev/sda5        27b4a69f-13ef-4be6-b539-cd480d1ce92a   crypto_LUKS 
/dev/sr0                                                iso9660    Ubuntu 13.10 amd64

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  f2 50 65 b1 70 4f f0 31  0c 71 e6 c8 92 aa 43 29  |.Pe.pO.1.q....C)|
00000010  5a 8a c6 4a d8 08 38 87  c0 21 8a ce 94 de 33 6c  |Z..J..8..!....3l|
00000020  41 1e 2e 8b 72 b7 de 7a  5a fe 27 c3 78 7f e9 ee  |A...r..zZ.'.x...|
00000030  e4 b3 9d 2d 6d f7 93 0f  75 2f 08 37 cf db a9 bb  |...-m...u/.7....|
00000040  a1 d9 4b 00 8f be 75 75  0d ad df 64 ac 01 c1 3d  |..K...uu...d...=|
00000050  48 59 e4 1c f0 1f e7 df  f8 af 95 18 5a 3b e8 02  |HY..........Z;..|
00000060  45 94 cb fc 69 5a 3d f3  d6 96 8d 12 9d ff 80 03  |E...iZ=.........|
00000070  dd 9e 9b 05 6e c4 b0 2a  19 e1 60 5e 80 8f a9 79  |....n..*..`^...y|
00000080  54 68 81 f3 0e c1 f0 66  45 b3 32 0d cb e5 d1 22  |Th.....fE.2...."|
00000090  e5 9f c7 42 d4 6d ec 3e  3e 5a 10 da 5f bc 3b ed  |...B.m.>>Z.._.;.|
000000a0  45 e4 32 29 c8 78 f0 6d  9e dd 75 e8 1a 85 ae 16  |E.2).x.m..u.....|
000000b0  b1 7f 55 16 ad 59 d7 f4  62 61 e7 9c 9b de 05 08  |..U..Y..ba......|
000000c0  a5 c7 c9 81 1c 0a 6b 05  0e bd 53 f2 c7 63 e9 6c  |......k...S..c.l|
000000d0  36 e2 f0 0b 56 0a 35 d3  a8 56 a0 b2 b2 30 46 f3  |6...V.5..V...0F.|
000000e0  06 cf 44 be 5e 30 64 dd  a7 08 58 fb ea b0 64 8b  |..D.^0d...X...d.|
000000f0  25 99 ad ac d2 61 1f b9  0d a0 f7 ae 59 d8 9d 1c  |%....a......Y...|
00000100  fe 80 f4 3f d2 dd 00 95  ad 1f 67 4f b0 ed 21 c2  |...?......gO..!.|
00000110  06 5d 1b ee 98 ed 4a 07  25 13 ee 28 31 88 01 f1  |.]....J.%..(1...|
00000120  b4 9c 9a 4b d7 c3 bb 2b  f1 ac 7b ef 78 d4 ff 17  |...K...+..{.x...|
00000130  53 05 21 da 28 3c f6 b7  b0 27 4a fa 92 4a 84 61  |S.!.(<...'J..J.a|
00000140  40 c0 8b 76 c8 c2 78 58  ee 5a f3 29 71 a8 27 c1  |@..v..xX.Z.)q.'.|
00000150  09 d2 50 a3 77 d4 72 97  44 2e 5f 1d 17 2f 61 70  |..P.w.r.D._../ap|
00000160  2f 08 00 2a dd 37 19 5d  49 21 70 5a c0 db 8c 9d  |/..*.7.]I!pZ....|
00000170  f8 64 c6 7a 06 3a 1c 5e  84 52 e1 44 e3 68 c3 6a  |.d.z.:.^.R.D.h.j|
00000180  63 ff 44 ea 92 73 6e 36  37 1e 86 65 b5 be da 56  |c.D..sn67..e...V|
00000190  9b 92 80 a3 c4 36 b9 65  f4 9b 26 e0 51 1a 46 5e  |.....6.e..&.Q.F^|
000001a0  b8 f6 f8 83 1b 95 ce d6  a9 11 9b 13 3e 59 17 cd  |............>Y..|
000001b0  92 c3 ab c2 ef bb 3e a0  bd 81 ef 84 ce 42 00 3b  |......>......B.;|
000001c0  1d 1f 83 fe ff ff 02 00  00 00 00 d8 7d 4a 00 00  |............}J..|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda5

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 36 34 00 00 00 00 00  00 00 00 00 00 00 00 00  |n64.............|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 10 00 00 00 00 40  |...............@|
00000070  ec 78 1e 66 4c 71 a7 32  a6 03 3d 1e eb 9a 5f 41  |.x.fLq.2..=..._A|
00000080  d4 b4 98 f7 0c b8 61 7d  9c 5d 45 e5 d8 6f 1a 72  |......a}.]E..o.r|
00000090  b1 41 cc ad 7b 57 cd 17  19 3a 75 24 96 b8 15 80  |.A..{W...:u$....|
000000a0  e2 97 18 e3 00 00 bb 80  32 37 62 34 61 36 39 66  |........27b4a69f|
000000b0  2d 31 33 65 66 2d 34 62  65 36 2d 62 35 33 39 2d  |-13ef-4be6-b539-|
000000c0  63 64 34 38 30 64 31 63  65 39 32 61 00 00 00 00  |cd480d1ce92a....|
000000d0  00 ac 71 f3 00 02 ee 42  b2 e5 57 43 f8 56 fd 1c  |..q....B..WC.V..|
000000e0  bc 11 18 0a 4f 87 31 5e  1e 40 e1 e8 4e 17 1c 18  |....O.1^.@..N...|
000000f0  e9 72 12 d9 43 41 61 0a  00 00 00 08 00 00 0f a0  |.r..CAa.........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 02 00 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 03 f8 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 05 f0 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 07 e8 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 09 e0 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
```

---

### Post by Kemper_Jacobs on 2014-02-17
This is what I got:



ubuntu@ubuntu:~$ sudo fsck -cc /dev/sda1
fsck from util-linux 2.20.1
e2fsck 1.42.8 (20-Jun-2013)
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                                 
/dev/sda1: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 18/62248 files (5.6% non-contiguous), 14646/248832 blocks

---

### Post by wildmanne39 on 2014-02-17
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Bucky Ball on 2014-02-17
Well, according to your boot info script you have no Windows on there and no grub anywhere. Can you actually get to a desktop by boot from the Live installer? If so, could you simply delete all partitions and try again?

---

### Post by Kemper_Jacobs on 2014-02-18
Tried the commands from requested fix from post #2...... still getting [Errno 5] input/output error. I am on the third burned Live cd. What next?

---

### Post by Bucky Ball on 2014-02-18
Posted in error. ;)

---

### Post by Kemper_Jacobs on 2014-02-18
So should I try to re-install a new grub?

---

### Post by deadflowr on 2014-02-18
> **Kemper_Jacobs said:**
> So should I try to re-install a new grub?

I would follow Bucky Ball's advice and wipe the partition table and try building them anew.
Probably see how a regular partition layout works before trying a crypto LUKS layout.
Make partition #1 /(root) and partition #2 extended and make partition #5 swap(linux-swap).
Basically letting the installer do this by choosing the option to wipe and install Ubuntu.
I think it's option one(maybe option two) in the installer.
Should say something like completely wipe and install Ubunut over whole disk.
See if it installs right after doing that.

---

### Post by Kemper_Jacobs on 2014-02-18
I just tried that and I am getting the same error.

---

