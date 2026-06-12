---
title: "Another Seagate Central 4tb failure. I'm so close - Please help"
date: 2015-09-05
forum: General Help
---

### Post by Zac_Brazdis on 2015-09-05
Hi All, 

First off, thank you all for the knowledge on this great forum. I've looked at **all** the old locked/solved posts regarding taking data off the Seagate Central HD and learned a great deal. I'm a Linux / Ubuntu beginner (soon to be novice, hopefully). I've sat at my computer for about 24 hours over the last two days trying to grab my data off my failed Seagate Central 4tb. It's important as I have a lot of client files stored on it, college / childhood photos, my little girls first steps... you get the idea.

Regardless, I went the Ubuntu USB boot route and installed fuseExt2 using the Terminal. I've updated it using the command strings as well. 

The part I'm having trouble with is the mounting part and understanding where to find the files to copy to the new HD (including the command prompt in Terminal). Just as an FYI - I'm running a BlacX Duet which holds two external hard drives and uses USB 3.0 and I'm planning to copy the files that way. SATA Drive 1 being the 4tb Seagate Central Drive - the other a Samsung 6TB drive as my laptop only has 2TB of storage and I have about 3TB on the actual Seagate Drive, so obviously backing up the data on my internal laptop drive wouldn't work. 

So - on to the part where I need help:

This is my last Terminal situation: 

```
Sudo fuseext2 -o ro -o allow_other /dev/mapper/vg1-lv1/mnt/seagateModel: JMicron  (scsi)
Disk /dev/sdd: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:
 
Number  Start   End    Size    File system  Name                Flags
 1      1049kB 22.0MB  21.0MB  ext2        Kernel_1            msftdata
 2      22.0MB 43.0MB  21.0MB  ext2        Kernel_2            msftdata
 3      43.0MB 1117MB  1074MB  ext4        Root_File_System_1  msftdata
 4      1117MB 2190MB  1074MB  ext4        Root_File_System_2  msftdata
 5      2190MB 3264MB  1074MB  ext4        Config              msftdata
 6      3264MB 4338MB  1074MB               Swap
 7      4338MB 5412MB  1074MB               Update              msftdata
** 8      5412MB 4001GB  3995GB               Data                lvm**
 
 
Error: /dev/mapper/vg1-lv1: unrecognised disk label
Warning: Error fsyncing/closing /dev/mapper/vg1-lv1: No suchdevice
Retry/Ignore? sudo fuseext2 -o ro -o allow_other/dev/mapper/vg1-lv1 /mnt/seagate
parted: invalid token: sudo
Retry/Ignore? r                                                          
Warning: Error fsyncing/closing /dev/mapper/vg1-lv1: No suchdevice
Retry/Ignore? i                                                          
Model: Linux device-mapper (linear) (dm)
**Disk /dev/mapper/vg1-lv1: 3995GB**
Sector size (logical/physical): 512B/512B
Partition Table: unknown

Disk Flags:
```

I've also looked at other blogs and form techniques - some which include fdisk which I don't want to risk. I've also heard someone tearing apart a new one and placing the HD in the new body and it worked without formatting the Seagate drive (which was my worry). Luckily I purchased this at Costco and I can return it for full price... after I get my data back of course. And for all this trouble, I'm keeping the HD and returning only the chasis and blown 

Anyway, if anyone out there can help me out, it would be huge and I'd be so grateful. Not only do I have client (I'm a web & graphic designer) but I also have college photos, tons of artwork, and my little girls first steps, etc... you get the idea. 

My "noob" questions are:

1. Once mounted, how can you tell? Can you actually see the files / data - or is it just a straight copy to the new HD? 

2. After it's mounted what would the Terminal command(s) be to start the data transfer to the new drive? 

On a positive note - I've learned a decent amount about Linux finally... and I'm really interested in learning more. 

A HUGE thanks to anyone that responds! Oh, and if anyone can recommend a new reliable Network Media Storage Drive for me, that would be great. 

Also if you'd like me to run any commands and post them, please let me know and I'll get them up ASAP!

Thanks in advance!

Zac B.

---

### Post by coldraven on 2015-09-05
I can't answer your questions because I know nothing about LVM partitions.
What I do know is that it is recommended to clone the faulty drive and then try to extract your data from the clone. That way if you mess it up you still have your original disc and can start again. There are some tips here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by howefield on 2015-09-05
Thread moved to the "*General Help*" forum for better support.

---

### Post by Zac_Brazdis on 2015-09-05
Thanks for the recommendations everyone and thanks howefield on the move... I was debating which section to post this. I know this topic has been covered a few times here... I'm just having trouble understanding how to mount this device then the command to copy the data partition to the new hard drive. I've been using these instructions and have installed LVM2 and FuseExt2... all updated. I've been generally [following these instructions]("http://myanwyn.blogspot.com/2014/08/how-to-recover-seagate-central-data.html"), which have helped me up greatly up until this point. TIA, Zac

---

### Post by oldfred on 2015-09-05
I do not know lvm nor Seagate drives.

But l and 1 look a lot alike and example looks like 1 (one) but your post looks like one of the one's is and l (el or L)?

Only with the very newest version of Ubuntu does fdisk version support gpt partitioned drives. Use gdisk or parted. But those only show the physical partitions not the LVM partitions inside the physical.

Do these show anything?
sudo pvdisplay
sudo lvdisplay
 sudo vgchange -ay

 
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
 [https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by Mark Phelps on 2015-09-05
> I've also heard someone tearing apart a new one and placing the HD in the new body and it worked without formatting the Seagate drive (which was my worry).I am surprised that worked, even for a minute.  The heads of modern hard drivers are VERY close to the platters, much closer than the thickness of a human hair.  One tiny speci of dust, even so small that you would not see it, could lodge there and cause a head crash -- destroying the drive.  HDDs are assembled in environments know as "clean rooms" so this can not happen.  I would NOT suggest even attempting to disassemble the drive.

---

### Post by MartyBuntu on 2015-09-05
> **Mark Phelps said:**
> I am surprised that worked, even for a minute.  The heads of modern hard drivers are VERY close to the platters, much closer than the thickness of a human hair.  One tiny speci of dust, even so small that you would not see it, could lodge there and cause a head crash -- destroying the drive.  HDDs are assembled in environments know as "clean rooms" so this can not happen.  I would NOT suggest even attempting to disassemble the drive.

I'm assuming they mean the controller board...and not the platters themselves...

---

### Post by oldfred on 2015-09-05
Years ago I saw the removing platters to a new identical drive fix. But even then with 40 or 100GB drives the user commented that it might only work for one boot as any dust would damage platters. And then both drives were destroyed.

Now TB sized drives are even more precise and often electronically aligned, so one drives controller may not work on another drives platter.

---

### Post by Zac_Brazdis on 2015-09-05
Yes I'm not opening the actual hard drive, but just opening the casing for the NSF Network System. It's a standard SATA port in the back. The Seagate enclosure has horrible heat exchange and most of the boards to connect to your ethernet to router, fry. Generally from what I've seen they last roughly 2 years. If anyone can help me out on this it would be great. 

Oldfred: I'll try those commands in just a bit. There are multiple threads on here that discuss Seagate CENTRAL recovery. I'm so close I just don't know the commands to mount the drive, and the command to copy to a new drive. I'll post the code results after running those commands. Thanks for your help. I'm getting desperate here. 

If any of you guys can look at this link and try to decipher it to me in a way I understand it would be great. Specifically just the end steps like I said, mounting the drive then copying to a new drive. [Click here for the Seagate Central recovery steps / commands.]("http://myanwyn.blogspot.com/2014/08/how-to-recover-seagate-central-data.html") 

Thanks in advance everyone. -Z

---

### Post by Zac_Brazdis on 2015-09-08
Ok - will this help anyone? Please? I've spent days on this, if anyone could get this right I'd even you a 20$ on Paypal. Latest codes ran:

```
root@ubuntu:/home/ubuntu# sudo parted -l
Model: ATA WDC WD5000LPVX-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  420MB  419MB   ntfs         Basic data partition          hidden, diag
 2      420MB   735MB  315MB   fat32        EFI system partition          boot, esp
 3      735MB   869MB  134MB                Microsoft reserved partition  msftres
 4      869MB   484GB  483GB   ntfs         Basic data partition          msftdata
 5      484GB   484GB  472MB   ntfs                                       hidden, diag
 6      484GB   500GB  16.0GB  ntfs         Basic data partition          hidden, diag


Model: HP v100w (scsi)
Disk /dev/sdb: 8020MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  8020MB  8020MB  fat32


sudo lvs /dev/mapper/vg1-lv1
Model: JMicron  (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                Flags
 1      1049kB  22.0MB  21.0MB  ext2         Kernel_1            msftdata
 2      22.0MB  43.0MB  21.0MB  ext2         Kernel_2            msftdata
 3      43.0MB  1117MB  1074MB  ext4         Root_File_System_1  msftdata
 4      1117MB  2190MB  1074MB  ext4         Root_File_System_2  msftdata
 5      2190MB  3264MB  1074MB  ext4         Config              msftdata
 6      3264MB  4338MB  1074MB               Swap
 7      4338MB  5412MB  1074MB               Update              msftdata
 8      5412MB  4001GB  3995GB               Data                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg1-lv1: 3995GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  3995GB  3995GB  ext4


root@ubuntu:/home/ubuntu# sudo lvs /dev/mapper/vg1-lv1
  /dev/sdc7: read failed after 0 of 4096 at 0: Input/output error
  /dev/sdc7: read failed after 0 of 4096 at 4096: Input/output error
  LV   VG   Attr       LSize Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv1  vg1  -wi-a----- 3.63t
```

---

### Post by Zac_Brazdis on 2015-09-08
But when I try to mount it... this happens

```
root@ubuntu:/home/ubuntu# sudo lvs /dev/mapper/vg1-lv1
  /dev/sdc7: read failed after 0 of 4096 at 0: Input/output error
  /dev/sdc7: read failed after 0 of 4096 at 4096: Input/output error
  LV   VG   Attr       LSize Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv1  vg1  -wi-a----- 3.63t                                                    
root@ubuntu:/home/ubuntu# sudo mkdir /mnt/seagate
mkdir: cannot create directory ‘/mnt/seagate’: File exists
root@ubuntu:/home/ubuntu# sudo mount -t ext4 -o ro /dev/mapper/vg1-lv1 /mnt/seagate
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-lv1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


```

---

### Post by CharlesA on 2015-09-08
That disk is hosed. The only way you will be able to get the data off of it is if you already had backups or are willing to spend a ton of money for data recovery services.

[ddrescue]("http://forensicswiki.org/wiki/Ddrescue") might be able to recover some of the data if you use it to make a byte-for-byte copy to another drive but typically when you are getting I/O errors, it means the physical disk is damaged.

EDIT: This might help, but it is referring to removable drives: [http://www.linuxtechi.com/fixing-lvm-io-errors/](http://www.linuxtechi.com/fixing-lvm-io-errors/)
[http://serverfault.com/questions/421776/removing-vg-and-lv-after-physical-drive-has-been-removed](http://serverfault.com/questions/421776/removing-vg-and-lv-after-physical-drive-has-been-removed)

EDIT2: What does dmesg | tail say?

---

### Post by Zac_Brazdis on 2015-09-08
Ok - 

So I made the mounting file on my internal laptop HD (it's only 500gb) 

The mounting location that I created is ```
mnt/seagate
```

Now when I try to mount the Seagate Central Drive using this command: ```
root@ubuntu:/home/ubuntu#  sudo fuseext2 -o ro -o allow_other dev/mapper/vg1/lv1 mnt/seagate


```

I get these results: ```
fuse-umfuse-ext2: version:'0.4', fuse_version:'29' [main (fuse-ext2.c:331)]
fuse-umfuse-ext2: Cannot mount dev/mapper/vg1/lv1 [parse_options (fuse-ext2.c:145)]

fuse-umfuse-ext2 0.4 29 - FUSE EXT2FS Driver

Copyright (C) 2008-2010 Alper Akcan <alper.akcan@gmail.com>
Copyright (C) 2009 Renzo Davoli <renzo@cs.unibo.it>
(The version number is for the VirtualSquare fork only)

Usage:    fuse-ext2 <device|image_file> <mount_point> [-o option[,...]]

Options:  ro, force, allow_others
          Please see details in the manual.


```

I've confirmed the mounting location is there - on my internal drive. Although I'm only running 500gb internal HD on my laptop... could this be a problem. It's simply saying it can not find the location I'm trying to copy it to... but I can find it on my internal drive. I'm losing it...

---

### Post by Zac_Brazdis on 2015-09-08
Charles A: Thanks for the recommendation. I can see the drive and it spins and reads fine, I can see the visible drive it's self - just not the data. 

Regardless if the drive is in fact bad, what would you recommend? Here's what the command says:

```
root@ubuntu:/home/ubuntu# dmesg | tail
[31584.049715] Read(16): 88 00 00 00 00 00 00 81 48 00 00 00 00 08 00 00
[31584.049754] blk_update_request: critical medium error, dev sdc, sector 8472576
[31956.517438] EXT4-fs (sdc2): mounting ext2 file system using the ext4 subsystem
[31956.531572] EXT4-fs (sdc2): warning: mounting unchecked fs, running e2fsck is recommended
[31956.532273] EXT4-fs (sdc2): mounted filesystem without journal. Opts: (null)
[31962.310322] EXT4-fs (sdc4): warning: maximal mount count reached, running e2fsck is recommended
[31962.310995] EXT4-fs (sdc4): mounted filesystem with ordered data mode. Opts: (null)
[31990.057069] EXT4-fs (sdc3): warning: maximal mount count reached, running e2fsck is recommended
[31990.057636] EXT4-fs (sdc3): mounted filesystem with ordered data mode. Opts: (null)
[33023.355989] EXT4-fs (dm-0): bad block size 65536


```

---

### Post by CharlesA on 2015-09-08
Run a fsck on it with it unmounted and see what it returns.

```
sudo fsck -fC /dev/sdc1
```

Do that for these partitions:
```
 1      1049kB  22.0MB  21.0MB  ext2         Kernel_1            msftdata
 2      22.0MB  43.0MB  21.0MB  ext2         Kernel_2            msftdata
 3      43.0MB  1117MB  1074MB  ext4         Root_File_System_1  msftdata
 4      1117MB  2190MB  1074MB  ext4         Root_File_System_2  msftdata
 5      2190MB  3264MB  1074MB  ext4         Config              msftdata
```

Then we can go from there. Hopefully fsck can recover the superblock and that'll let you mount the drive.

---

### Post by Zac_Brazdis on 2015-09-08
So is this drive "bad" (I don't think it is as I can access all the infrastructure, user folders, etc... but obviously not the actual data that I want since you can only get it through the method I'm using. It spins perfect, no abnormal noises, etc... 

This HD has about 2TB of actual data out of roughly 4tb of actual capacity. So since I'm trying to mount it to a 500GB hard drive, would that possibly cause the "warning: maximal mount count reached"? I'm going out to grab a larger drive to mount (my enclosure houses 2 internal HD's. I currently only have the Seagate Central 4TB on it which worked the night before the ethernet NAS chip fried (which happens to ALL of these things - called the "blinking green light of death". We'll see what happens wednesday. I ordered another identical Seagate Central 4tb. I returned my other without the internal HD and got a full refund of a bit over $200 at Costco, so no real money lost here since I purchased the new one from Amazon Prime for $100 and change. 

Reason I did that was because I found a few people having success by opening the new device, swapping HD's and supposedly it works just fine. I was concerned it may format it automatically and I'd lose my data. I guess we will find out. 
[B]
So I guess my question is, can I mount this 4tb device to a 500gb laptop drive? Could that be the issue here? [/B]

Thanks in advance and to everyone else who's assisted me in this mess. -Z

---

### Post by Zac_Brazdis on 2015-09-08
Charles - I'll try that now and see what happens. I'll report back in a moment with the results.

---

### Post by Zac_Brazdis on 2015-09-08
> **CharlesA said:**
> Run a fsck on it with it unmounted and see what it returns.

```
sudo fsck -fC /dev/sdc1
```

Do that for these partitions:
```
 1      1049kB  22.0MB  21.0MB  ext2         Kernel_1            msftdata
 2      22.0MB  43.0MB  21.0MB  ext2         Kernel_2            msftdata
 3      43.0MB  1117MB  1074MB  ext4         Root_File_System_1  msftdata
 4      1117MB  2190MB  1074MB  ext4         Root_File_System_2  msftdata
 5      2190MB  3264MB  1074MB  ext4         Config              msftdata
```

Then we can go from there. Hopefully fsck can recover the superblock and that'll let you mount the drive.

Ok, sorry for being such a noob here with this... I unmounted, ran the command, but how do you define the partition? is it just "sdc1 then sdc2, etc, etc...? 

I ran your code (sudo fsck -fC /dev/sdc1) after unmounting and here's what I got:

```
root@ubuntu:/home/ubuntu# sudo fsck -fC /dev/sdc1
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
fsck.ext2: No such file or directory while trying to open /dev/sdc1
Possibly non-existent device?
root@ubuntu:/home/ubuntu# sudo fsck -fC /dev/sdc2
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
fsck.ext2: No such file or directory while trying to open /dev/sdc2
Possibly non-existent device?
root@ubuntu:/home/ubuntu# sudo fsck -fC /dev/sdc3
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
fsck.ext2: No such file or directory while trying to open /dev/sdc3
Possibly non-existent device?


```

If I'm entering this wrong by defining the specific partitions, could you give me an exact code example with one of the partitions so I can be sure? Thanks again!

---

### Post by CharlesA on 2015-09-08
It might be different because it's lvm. I always use the UUID when I run a fsck instead of the device name.

Run this:

```
sudo fdisk -l
```

```
sudo blkid -c /dev/null
```

EDIT: As far as mounting goes. The only thing you are doing is telling the OS where to "mount" the drive - for example in /mnt/seagate

This is similar to the way Windows puts each drive under it's own letter. C:, D:. E:, etc.

It isn't copying anything to the other drive, just giving you a way to access the contents of the drive through whatever path you mounted it to. Hope that makes sense.

---

### Post by Zac_Brazdis on 2015-09-08
> **CharlesA said:**
> It might be different because it's lvm. I always use the UUID when I run a fsck instead of the device name.

Run this:

```
sudo fdisk -l
```

```
sudo blkid -c /dev/null
```

EDIT: As far as mounting goes. The only thing you are doing is telling the OS where to "mount" the drive - for example in /mnt/seagate

This is similar to the way Windows puts each drive under it's own letter. C:, D:. E:, etc.

It isn't copying anything to the other drive, just giving you a way to access the contents of the drive through whatever path you mounted it to. Hope that makes sense.

Got you on that. Thanks for making that clear on how it's just mounting and space wont be an issue. Here's the code from your first command:

 ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/loop0: 1 GiB, 1101672448 bytes, 2151704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/loop1: 4 GiB, 4287627264 bytes, 8374272 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: 20464D32-AB27-4241-A2CA-0B121BF7E087

Device        Start        End    Sectors  Size Type
/dev/sda1      2048      43007      40960   20M Microsoft basic data
/dev/sda2     43008      83967      40960   20M Microsoft basic data
/dev/sda3     83968    2181119    2097152    1G Microsoft basic data
/dev/sda4   2181120    4278271    2097152    1G Microsoft basic data
/dev/sda5   4278272    6375423    2097152    1G Microsoft basic data
/dev/sda6   6375424    8472575    2097152    1G Linux swap
/dev/sda7   8472576   10569727    2097152    1G Microsoft basic data
/dev/sda8  10569728 7814037134 7803467407  3.6T Linux LVM

Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 11236BC5-8CC0-4E62-AC15-FF60126B3557

Device         Start       End   Sectors   Size Type
/dev/sdb1       2048    821247    819200   400M Windows recovery environment
/dev/sdb2     821248   1435647    614400   300M EFI System
/dev/sdb3    1435648   1697791    262144   128M Microsoft reserved
/dev/sdb4    1697792 944658431 942960640 449.7G Microsoft basic data
/dev/sdb5  944658432 945580031    921600   450M Windows recovery environment
/dev/sdb6  945580032 976773119  31193088  14.9G Windows recovery environment

Disk /dev/sdc: 7.5 GiB, 8019509248 bytes, 15663104 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x20ac7dda

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sdc1  ?    3224498923 3657370039  432871117 206.4G  7 HPFS/NTFS/exFAT
/dev/sdc2  ?    3272020941 5225480974 1953460034 931.5G 16 Hidden FAT16
/dev/sdc3  ?             0          0          0     0B 6f unknown
/dev/sdc4         50200576  974536369  924335794 440.8G  0 Empty

Partition table entries are not in disk order.
Disk /dev/mapper/vg1-lv1: 3.6 TiB, 3995372355584 bytes, 7803461632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
ubuntu@ubuntu:~$ 

```

---

### Post by Zac_Brazdis on 2015-09-08
And your second command below (thanks so much for helping). My little girls first steps are on this damn thing... TIA

Give me your thoughts on this:

```
ubuntu@ubuntu:~$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs"
/dev/loop1: LABEL="casper-rw" UUID="9300ce26-984a-3545-bf38-0b05630cf85e" TYPE="ext2"
/dev/sda1: UUID="146a5605-2387-4c5c-afc0-dd505ccc3f69" TYPE="ext2" PARTLABEL="Kernel_1" PARTUUID="b18fe161-54fb-496e-82ee-25e67ec7a987"
/dev/sda2: UUID="6d9403c0-bcc0-4418-bb72-b62794f0176a" TYPE="ext2" PARTLABEL="Kernel_2" PARTUUID="5e95c8ef-1e27-4d09-a977-9819457fac67"
/dev/sda3: UUID="2e735ec8-7b19-483b-8598-54aeb9f57ae7" TYPE="ext4" PARTLABEL="Root_File_System_1" PARTUUID="f6b67ed4-9869-46ed-9ea4-91b2565171c9"
/dev/sda4: UUID="0b04e63f-df53-47c4-85ee-b61a95a80ba0" TYPE="ext4" PARTLABEL="Root_File_System_2" PARTUUID="2c96a290-739f-413f-a63c-8b63bfce33a4"
/dev/sda5: LABEL="Config" UUID="9529d2cb-45de-4c4e-9f50-ab34b6ba6210" TYPE="ext4" PARTLABEL="Config" PARTUUID="a061a7d9-854d-43a3-a951-ab7732c1ac02"
/dev/sda6: LABEL="Swap" UUID="a572b508-deb0-4201-81d2-9c97037f26fe" TYPE="swap" PARTLABEL="Swap" PARTUUID="974a1187-c52b-4a28-8370-8bdc96e033f4"
/dev/sda8: UUID="pv7XTd-G8nk-XxTc-qUBG-rxjB-4ZL2-CHPzGr" TYPE="LVM2_member" PARTLABEL="Data" PARTUUID="b45b9eb8-679e-4ac9-ae2d-49fde623f08e"
/dev/sdb1: LABEL="Recovery" UUID="74DC44BCDC447A7E" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="a4a5142c-4a40-4132-8463-48ac7e3410d2"
/dev/sdb2: LABEL="ESP" UUID="F447-1B9E" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="f5193e49-db80-49b3-b1d0-3f5deafffcdf"
/dev/sdb3: PARTLABEL="Microsoft reserved partition" PARTUUID="564962e1-f578-41de-82a2-64a45e8fd714"
/dev/sdb4: LABEL="Acer" UUID="2E48487D484845B5" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="b3e0db2c-373d-4787-ace1-855a91e702ef"
/dev/sdb5: UUID="864AE7264AE711AB" TYPE="ntfs" PARTUUID="c0d554ef-b9db-4af7-825d-cbad4fd830d4"
/dev/sdb6: LABEL="Push Button Reset" UUID="C0CC4A1ACC4A0ADC" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="ad5f8c4f-d07a-488c-95c1-0d1f426ba35a"
/dev/mapper/vg1-lv1: LABEL="Data" UUID="c354b521-bcd5-494b-9679-0dc2e66b5dd6" TYPE="ext4"
/dev/sdc: LABEL="UUI" UUID="403E-3C4A" TYPE="vfat"


```

---

### Post by Zac_Brazdis on 2015-09-08
I've notice people having issues actually mounting it to the created directory, that's where I am stuck. The directory exist on my internal lap top HD in "/mnt/seagate" but it says that the location doesn't exist when trying to mount. Do I need to put "C:/" or anything like that before "/mnt/seagate"

And just for your reference, I ran "Sudo parted -l" if this is helpful to you:

```
ubuntu@ubuntu:~$ sudo parted -l
Model: JMicron  (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                Flags
 1      1049kB  22.0MB  21.0MB  ext2         Kernel_1            msftdata
 2      22.0MB  43.0MB  21.0MB  ext2         Kernel_2            msftdata
 3      43.0MB  1117MB  1074MB  ext4         Root_File_System_1  msftdata
 4      1117MB  2190MB  1074MB  ext4         Root_File_System_2  msftdata
 5      2190MB  3264MB  1074MB  ext4         Config              msftdata
 6      3264MB  4338MB  1074MB               Swap
 7      4338MB  5412MB  1074MB               Update              msftdata
 8      5412MB  4001GB  3995GB               Data                lvm


Model: ATA WDC WD5000LPVX-2 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  420MB  419MB   ntfs         Basic data partition          hidden, diag
 2      420MB   735MB  315MB   fat32        EFI system partition          boot, esp
 3      735MB   869MB  134MB                Microsoft reserved partition  msftres
 4      869MB   484GB  483GB   ntfs         Basic data partition          msftdata
 5      484GB   484GB  472MB   ntfs                                       hidden, diag
 6      484GB   500GB  16.0GB  ntfs         Basic data partition          hidden, diag


Model: HP v100w (scsi)
Disk /dev/sdc: 8020MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  8020MB  8020MB  fat32


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg1-lv1: 3995GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  3995GB  3995GB  ext4


```

---

### Post by CharlesA on 2015-09-08
That's really weird.

Here's what I get on my server (using lvm):
```

sudo fdisk -l
Disk /dev/sda: 9000.1 GB, 9000103968768 bytes
255 heads, 63 sectors/track, 1094200 cylinders, total 17578328064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1               1  4294967295  2147483647+  ee  GPT**
Partition 1 does not start on physical sector boundary.

```

```
sudo blkid -c /dev/null
/dev/sda1: UUID="rYpYn8-QFm6-flQx-Gdqv-oWkj-qUkF-Dlyek4" TYPE="LVM2_member"
/dev/mapper/Thor-Array: UUID="05c730b5-680d-4d33-8e2e-76947d7a93fa" TYPE="ext4"

```

I was able to run a fsck on that partition by running this:

```
sudo fsck -Cf UUID=05c730b5-680d-4d33-8e2e-76947d7a93fa
```

Aside from the output of your fdisk and blkid looking off, you should theoretically be able to run fsck on that device by running this:

```
sudo fsck -Cf UUID=c354b521-bcd5-494b-9679-0dc2e66b5dd6
```

---

### Post by Zac_Brazdis on 2015-09-08
Charles - thank you so much for your help here, really, I couldn't do this without you. 

I ran the command you told me to run, here's what I got. Hopefully good info. Should I fix (y) or (n), I'm assuming yes. But just waiting for your advice. I'll leave Terminal running at there for now. 

```
ubuntu@ubuntu:~$ sudo fsck -Cf UUID=c354b521-bcd5-494b-9679-0dc2e66b5dd6
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
Data: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts
Pass 5: Checking group summary information                                     
Free blocks count wrong (43128587, counted=43127616).                          
Fix<y>? 


```

---

### Post by CharlesA on 2015-09-08
Go ahead and fix it.

There will likely be other errors, but if you are unsure about them, go ahead and put the output in your next post.

Hopefully fsck can repair the file system and you can get to your data.

---

### Post by Zac_Brazdis on 2015-09-08
Will do, thanks. PM me your Paypal if you have one. You've been such a big help. I'll post up my results in a half hour or so. Thanks again, Z

---

### Post by Zac_Brazdis on 2015-09-08
Hey Charles, well that was faster than I expected... 

Here are my results. Shall I try to mount the drive now? If you have the time, could you confirm the best way to do it? I believe I was doing it right but it kept saying that the folder mgt/seagate (which I created on my C: internal HD) was not there. 

Let me know!

```
ubuntu@ubuntu:~$ sudo fsck -Cf UUID=c354b521-bcd5-494b-9679-0dc2e66b5dd6
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
Data: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts
Pass 5: Checking group summary information                                     
Free blocks count wrong (43128587, counted=43127616).                          
Fix<y>? yes
Free inodes count wrong (60688604, counted=60687751).                          
Fix<y>? yes

Data: ***** FILE SYSTEM WAS MODIFIED *****
Data: 87929/60775680 files (9.3% non-contiguous), 17836928/60964544 blocks


```

---

### Post by CharlesA on 2015-09-08
> **Zac_Brazdis said:**
> Will do, thanks. PM me your Paypal if you have one. You've been such a big help. I'll post up my results in a half hour or so. Thanks again, Z

Don't worry about it.

> **Zac_Brazdis said:**
> Hey Charles, well that was faster than I expected... 

Here are my results. Shall I try to mount the drive now? If you have the time, could you confirm the best way to do it? I believe I was doing it right but it kept saying that the folder mgt/seagate (which I created on my C: internal HD) was not there. 

Let me know!

```
ubuntu@ubuntu:~$ sudo fsck -Cf UUID=c354b521-bcd5-494b-9679-0dc2e66b5dd6
fsck from util-linux 2.25.2
e2fsck 1.42.12 (29-Aug-2014)
Data: recovering journal
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure                                           
Pass 3: Checking directory connectivity                                        
Pass 4: Checking reference counts
Pass 5: Checking group summary information                                     
Free blocks count wrong (43128587, counted=43127616).                          
Fix<y>? yes
Free inodes count wrong (60688604, counted=60687751).                          
Fix<y>? yes

Data: ***** FILE SYSTEM WAS MODIFIED *****
Data: 87929/60775680 files (9.3% non-contiguous), 17836928/60964544 blocks


```

Yeah, go ahead and try the mount the drive. I don't see any errors about the superblock, but maybe it'll mount this time.

---

### Post by Zac_Brazdis on 2015-09-08
Ok, so to mount I'm going to run this command - if you see any issues with it please let me know. Thanks so much - you have no idea... my little girls first steps, college pictures, movie collection, etc... I owe you big time.

I ran this command to mount and this is what I got: 
```
ubuntu@ubuntu:~$ sudo mount -a
ubuntu@ubuntu:~$ sudo fuseext2 -o ro -o allow_other /dev/mapper/vg1-lv1 /mnt/seagate
fuse-umfuse-ext2: version:'0.4', fuse_version:'29' [main (fuse-ext2.c:331)]
fuse-umfuse-ext2: enter [do_probe (do_probe.c:30)]
fuse-umfuse-ext2: leave [do_probe (do_probe.c:55)]
fuse-umfuse-ext2: opts.device: /dev/mapper/vg1-lv1 [main (fuse-ext2.c:358)]
fuse-umfuse-ext2: opts.mnt_point: /mnt/seagate [main (fuse-ext2.c:359)]
fuse-umfuse-ext2: opts.volname: Data [main (fuse-ext2.c:360)]
fuse-umfuse-ext2: opts.options: ro,allow_other [main (fuse-ext2.c:361)]
fuse-umfuse-ext2: parsed_options: allow_other,ro,fsname=/dev/mapper/vg1-lv1 [main (fuse-ext2.c:362)]
fuse-umfuse-ext2: mounting read-only [main (fuse-ext2.c:378)]


```

---

### Post by Zac_Brazdis on 2015-09-08
Darn, C: is empty in /mgt/seagate. Did it mount? Should I try a different way to mount it or should I run as a root user?

---

### Post by Zac_Brazdis on 2015-09-08
Actually I have a circling "Loading" in the bottom corner when I click the "mnt" folder. I have about 2TB full (of 4tb total)... is this normal for it to take this long to load the data? Or any other ideas? Thanks so much. Z

---

### Post by Zac_Brazdis on 2015-09-08
The external Seagate is spinning and the lights on my USB Ubuntu stick are flashing as well... fingers crossed. :KS

---

### Post by Zac_Brazdis on 2015-09-08
Wow, still loading also I tried remounting and it's still actively mounting as there is no "ubuntu@ubuntu~$" prompt yet. Is this normal? Eh...

---

### Post by ventrical on 2015-09-08
> **Zac_Brazdis said:**
> 
[B]
So I guess my question is, can I mount this 4tb device to a 500gb laptop drive? Could that be the issue here? [/B]

Thanks in advance and to everyone else who's assisted me in this mess. -Z

Yes .. you can mount it on most any SATA PC (think you would need a SATA to USB bridge here). I have a 3TB Seagate SATA III Barracuda and I can swap it on any machine as long as I am not trying to load windows 8 or 10.  If you have a desktop tower I would use that to mount the 4TB hdd .. even with an 80GB drive .. but of course you will need larger to copy your files over because of large collection of data. All I do is drag and drop. I do not use any programs .. just bare ubuntu already has what you need. I can access any drive .. even locked drives or drives that are supposssed to be bricked. Of course some drives do get bricked but I think you are ok and that you are just going to fast .. so take a back step and review.?

Regards..

---

### Post by ventrical on 2015-09-08
Ok .. see where CharlesA is working on this..:)

Regards..

---

### Post by Zac_Brazdis on 2015-09-08
yeah still loading. Generally how long should this take to mount in terminal. Terminal is still "actively processing" or whatever. It's been an hour.

---

### Post by ventrical on 2015-09-08
I would have aborted 55 minutes ago :) but looks like CharlesA  is trying to help so I do not want to  confuse you with other instructions. Do you have SATA to USB  bridge?

---

### Post by CharlesA on 2015-09-08
> **Zac_Brazdis said:**
> Darn, C: is empty in /mgt/seagate. Did it mount? Should I try a different way to mount it or should I run as a root user?

Erm, that doesn't sound good. Can you post the output, assuming it actually mounted?

> **Zac_Brazdis said:**
> Actually I have a circling "Loading" in the bottom corner when I click the "mnt" folder. I have about 2TB full (of 4tb total)... is this normal for it to take this long to load the data? Or any other ideas? Thanks so much. Z

It shouldn't take very long to read the data assuming it mounted correctly. Do you still anything in dmesg?

> **ventrical said:**
> Ok .. see where CharlesA is working on this..:)

Regards..

You can always chime in if you have any other ideas. :)

> **Zac_Brazdis said:**
> yeah still loading. Generally how long should this take to mount in terminal. Terminal is still "actively processing" or whatever. It's been an hour.

Doesn't bode well at all. The mount itself should only take a few seconds.

If you have another drive that is the same size, I would recommend using ddrescue to copy the data from the bad drive to the other one before you do anything else. I have a feeling the other drive is toast - the read errors. Issues mounting and other stuff, but the first thing to do is to get a copy of the data off the drive in case the drive fails entirely.

---

### Post by ventrical on 2015-09-08
> **Zac_Brazdis said:**
> Hi All, 

First off, thank you all for the knowledge on this great forum. I've looked at **all** the old locked/solved posts regarding taking data off the Seagate Central HD and learned a great deal. I'm a Linux / Ubuntu beginner (soon to be novice, hopefully). I've sat at my computer for about 24 hours over the last two days trying to grab my data off my failed Seagate Central 4tb. It's important as I have a lot of client files stored on it, college / childhood photos, my little girls first steps... you get the idea.

Regardless, I went the Ubuntu USB boot route and installed fuseExt2 using the Terminal. I've updated it using the command strings as well. 


You said you have "updated it using the command strings as well". What were those command strings?

2. Did you use a live ubuntu-desktop USB stick to boot or pesistive?
3. What version of Ubuntu did you use ..ie 14.04 ?

The reason I ask is that there may be a slim chance that Grub updated something  (if you were using persistive drive).

Regards..

---

### Post by ventrical on 2015-09-08
> **CharlesA said:**
> Erm, that doesn't sound good. Can you post the output, assuming it actually mounted?



It shouldn't take very long to read the data assuming it mounted correctly. Do you still anything in dmesg?



You can always chime in if you have any other ideas. :)



Doesn't bode well at all. The mount itself should only take a few seconds.

If you have another drive that is the same size, I would recommend using ddrescue to copy the data from the bad drive to the other one before you do anything else. I have a feeling the other drive is toast - the read errors. Issues mounting and other stuff, but the first thing to do is to get a copy of the data off the drive in case the drive fails entirely.

+ ! :)

 I am assuming that Grub updated! After the OP #1 and if it was persistive USB. But other data shows that the folder should pop right up and he can  MOVE/COPY all those files to new drive.  


1. I would hard install ubuntu-desktop on 80GB or 200GB hdd or whatever. Use surplus hdd hanging around. 
2. After install, boot up installation. Connect USB drives and they should all come up and he could just :
```

sudo nautilus

```

and then just move all those folders to new drive.

 I did notice that there was one report of non contiguous files or other .. and a flag went up!

Regards..

---

### Post by Zac_Brazdis on 2015-09-08
Thanks everyone. About installing the full version, do I install to my internal HD or should install to a external? I have a 500gb laying around.

But, yeah... I aborted, restarted, removed ext HD, installed it again. Check out the end of this code and tell me what you think: 

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000LPVX-2 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  420MB  419MB   ntfs         Basic data partition          hidden, diag
 2      420MB   735MB  315MB   fat32        EFI system partition          boot, esp
 3      735MB   869MB  134MB                Microsoft reserved partition  msftres
 4      869MB   484GB  483GB   ntfs         Basic data partition          msftdata
 5      484GB   484GB  472MB   ntfs                                       hidden, diag
 6      484GB   500GB  16.0GB  ntfs         Basic data partition          hidden, diag


Model: HP v100w (scsi)
Disk /dev/sdb: 8020MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  8020MB  8020MB  fat32


Model: JMicron  (scsi)
Disk /dev/sdd: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                Flags
 1      1049kB  22.0MB  21.0MB  ext2         Kernel_1            msftdata
 2      22.0MB  43.0MB  21.0MB  ext2         Kernel_2            msftdata
 3      43.0MB  1117MB  1074MB  ext4         Root_File_System_1  msftdata
 4      1117MB  2190MB  1074MB  ext4         Root_File_System_2  msftdata
 5      2190MB  3264MB  1074MB  ext4         Config              msftdata
 6      3264MB  4338MB  1074MB               Swap
 7      4338MB  5412MB  1074MB               Update              msftdata
 8      5412MB  4001GB  3995GB               Data                lvm


Error: /dev/mapper/vg1-lv1: unrecognised disk label
Warning: Error fsyncing/closing /dev/mapper/vg1-lv1: No such device
Retry/Ignore? r                                                           
Warning: Error fsyncing/closing /dev/mapper/vg1-lv1: No such device
Retry/Ignore? r                                                           
Warning: Error fsyncing/closing /dev/mapper/vg1-lv1: No such device
Retry/Ignore? i                                                           
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg1-lv1: 3995GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


```

---

### Post by Zac_Brazdis on 2015-09-08
I just don't get how the NAS portion of the device can go AT the same time as the HD. I hate Seagate. I returned the shell to Costco and got a full refund (bought 2.5 years ago), refund of $210. So I went ahead and bought another exact Seagate Central 4TB to see if I could just swap the drives as I heard people having success with that. (I can always return to Amazon as I'm a Prime member. The new Seagate Central 4TB gets here tomorrow. 

Should I repair the block again? I'm at a loss.

---

### Post by ventrical on 2015-09-08
> **Zac_Brazdis said:**
> Thanks everyone. About installing the full version, do I install to my internal HD or should install to a external? I have a 500gb laying around.



[/CODE]

YEs!!  Internal is best. Take other drives out (disconnect them). Use whole disk(don't worry about partitions right now.) Get the install done to 500GB laying around and then get back to us.

Regards..

---

### Post by ventrical on 2015-09-08
Zac!! Help me out! What version number of ubuntu are you using .. what distro cycle?? Trusty ??

---

### Post by CharlesA on 2015-09-08
> **Zac_Brazdis said:**
> I just don't get how the NAS portion of the device can go AT the same time as the HD. I hate Seagate. I returned the shell to Costco and got a full refund (bought 2.5 years ago), refund of $210. So I went ahead and bought another exact Seagate Central 4TB to see if I could just swap the drives as I heard people having success with that. (I can always return to Amazon as I'm a Prime member. The new Seagate Central 4TB gets here tomorrow. 

Should I repair the block again? I'm at a loss.

I would make a backup of the existing drive before doing anything in the event putting the drive in the new NAS wipes the data or makes no difference at all.

Have you been able to mount the drive as read only since you unplugged it and plugged it back in?

---

### Post by Zac_Brazdis on 2015-09-08
Let me wipe this 500gb, install the full version of ubuntu on it and try nautilus. If anyone could give me a few commands to run in the mean time, that would be awesome. 

TIA!

---

### Post by Zac_Brazdis on 2015-09-08
Charles, yes, I'll make a copy of the drive before trying this. Thanks for the advice. :)

---

### Post by oldfred on 2015-09-08
Be sure to use Something Else if over installing an existing install. And be sure to use UEFI if original install is UEFI.

I think Seagate must do something proprietary with these drives. Says 64K block size?
And then your original link seems to be the only way to mount it with the fuseext2 driver
Another thread with two users and no solution:
[http://ubuntuforums.org/showthread.php?t=2198460&page=2](http://ubuntuforums.org/showthread.php?t=2198460&page=2)
Says solved but no conclusive post?
[URL="http://ubuntuforums.org/showthread.php?t=2199589"]http://ubuntuforums.org/showthread.php?t=2199589

[/URL][http://www.theregister.co.uk/2014/11/21/the_cloud_that_goes_puff_seagate_central_home_nas_woes/](http://www.theregister.co.uk/2014/11/21/the_cloud_that_goes_puff_seagate_central_home_nas_woes/)

---

### Post by CharlesA on 2015-09-09
> **oldfred said:**
> 
I think Seagate must do something proprietary with these drives. Says 64K block size?
And then your original link seems to be the only way to mount it with the fuseext2 driver

They must. I don't think I've ever used a fuseext2 drive before.

I did a quick search and found a few people recommending [r-linux]("http://www.r-tt.com/free_linux_recovery/") to try to recover the files on the drive, but the most common fix seems to be getting a new chassis and swapping drives.

Note to self, do not get one of these devices.

---

### Post by ventrical on 2015-09-09
> **CharlesA said:**
> They must. I don't think I've ever used a fuseext2 drive before.

I did a quick search and found a few people recommending [r-linux]("http://www.r-tt.com/free_linux_recovery/") to try to recover the files on the drive, but the most common fix seems to be getting a new chassis and swapping drives.

Note to self, do not get one of these devices.

Ahhhhhh....... :)

Regards..

---

### Post by Zac_Brazdis on 2015-09-09
Yes it is a 64kb block size from my research.   So I've installed the full version of ubuntu 14.04.3 LTS (with a lot of errors non the less), I downloaded the ubuntu version 15.04-desktop-amd64.iso - as I am running a AMD64 machine. I think I'm going to install this version.   For example, when I typed in code "sudo apt-get install fuseext2" it couldn't locate it... eh.   I'll be back on tonight, hopefully helps some of you out with the version I'm running.   Thanks for everything so far guys.

---

### Post by Zac_Brazdis on 2015-09-09
Hey Guys, 

I think this drive is toast or the file structure is gonzo. I don't know. I cant even run ```
sudo parted -l
```... it just hangs on trying to read the drive and I have to abort Terminal. 

The only thing I can get it to do is this, any ideas or advice on where to go from here? TIA 

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xfdc039f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
255 heads, 63 sectors/track, 1946 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03347bcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    31266815    15633392    c  W95 FAT32 (LBA)

Disk /dev/mapper/ubuntu--vg-root: 493.5 GB, 493455671296 bytes
255 heads, 63 sectors/track, 59992 cylinders, total 963780608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 5842 MB, 5842665472 bytes
255 heads, 63 sectors/track, 710 cylinders, total 11411456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.
ubuntu@ubuntu:~$ 


```

---

### Post by oldfred on 2015-09-09
Older versions of Ubuntu do not have an fdisk that works with gpt partitioned drives. So not seeing it from fdisk should be normal. I think the version in 15.04 may work, but know the version of fdisk in future 15.10 does work with gpt.

And with LVM you may have to install the lvm2 driver.
If using a live installer you have to install it each time you reboot. Newer
And go thru the process of mounting & opening the lvm to see the lvm partitions.

---

### Post by Zac_Brazdis on 2015-09-09
> **oldfred said:**
> Older versions of Ubuntu do not have an fdisk that works with gpt partitioned drives. So not seeing it from fdisk should be normal. I think the version in 15.04 may work, but know the version of fdisk in future 15.10 does work with gpt.

And with LVM you may have to install the lvm2 driver.
If using a live installer you have to install it each time you reboot. Newer
And go thru the process of mounting & opening the lvm to see the lvm partitions.

Yes, thanks for the info. Very valuable. I've decided to dedicate this computer to Ubuntu/Linux as it is a spare... small touch screen lap top. I overwrote windows as well. 

I did notice that after any reboot you have to reinstall the LVM2 driver. I'll do that and report back tonight. 

On I side note, my new Seagate Central 4TB arrived today. I plan or running it with a small fan 24/7 to help regulate temperature a bit (much actually) better. I'll deal with installing LVM2 driver after dinner and see what happens.

Thanks everyone for knowledge. Looks like now that I have a dedicated linux machine I'll be on here more often. ;):D

One question - which version of Ubuntu would you all recommend? I I'm running 14.04.3 LTS but I have downloaded 15.04 and was thinking of installing that. TIA -Z

---

### Post by oldfred on 2015-09-09
I have both installed. :)

But consider the LTS versions as my main working install as long as my hardware works with it.
Some very new hardware needs the newest version of Ubuntu or even newer as it takes a bit before open source developers can figure out new hardware. Very little support from many vendors.

---

### Post by CharlesA on 2015-09-09
Seconding the LTS versions, even though I mostly run Debian now.

Hope you are able to pull your data off of it.

---

### Post by Zac_Brazdis on 2015-09-10
Thank you guys for the version info. I'll be back at this tomorrow. Any of you think I should open my new Seagate Central 4tb NAS housing and swap out the drives and see if I can access it again via network? Feedback on that would be great. Someone stated they did just that after spending a few days trying to get it via Ubuntu, with LVM and FuseExt2.

TIA

---

### Post by Zac_Brazdis on 2015-09-10
FINALLY - "Sudo parted -l" didn't freeze up the terminal when executed. Here's what I have now:

```
Model: JMicron  (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                Flags
 1      1049kB  22.0MB  21.0MB  ext2         Kernel_1            msftdata
 2      22.0MB  43.0MB  21.0MB  ext2         Kernel_2            msftdata
 3      43.0MB  1117MB  1074MB  ext4         Root_File_System_1  msftdata
 4      1117MB  2190MB  1074MB  ext4         Root_File_System_2  msftdata
 5      2190MB  3264MB  1074MB  ext4         Config              msftdata
 6      3264MB  4338MB  1074MB               Swap
 7      4338MB  5412MB  1074MB               Update              msftdata
 8      5412MB  4001GB  3995GB               Data                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg1-lv1: 3995GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  3995GB  3995GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 5843MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  5843MB  5843MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 493GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  493GB  493GB  ext4



```

Drive bad? Drive good? Any thoughts on what to run next? Block repair again? Or just try and mount it.

---

### Post by CharlesA on 2015-09-10
Try mounting it and see what happens.

```
sudo mount /dev/mapper/vg1-lv1 /mnt/
```

---

### Post by ventrical on 2015-09-10
> **Zac_Brazdis said:**
> Thank you guys for the version info. I'll be back at this tomorrow. Any of you think I should open my new Seagate Central 4tb NAS housing and swap out the drives and see if I can access it again via network? Feedback on that would be great. Someone stated they did just that after spending a few days trying to get it via Ubuntu, with LVM and FuseExt2.

TIA

No.

 Just try to familiarize yourself with your new ubuntu install and navigate around a bit and get the feel of it. As I see it you should be able to access those files and drag em elsewhere but looks like you are in good hands as it is.

Long ago , while working on my Sanyo MBC 550 with MS-DOS 1.25 an instructor told me that  I had to 'learn how to make it walk before I could make it dance'. :)

Regards..

---

### Post by CharlesA on 2015-09-10
> **ventrical said:**
> No.

 Just try to familiarize yourself with your new ubuntu install and navigate around a bit and get the feel of it. As I see it you should be able to access those files and drag em elsewhere but looks like you are in good hands as it is.

Long ago , while working on my Sanyo MBC 550 with MS-DOS 1.25 an instructor told me that  I had to 'learn how to make it walk before I could make it dance'. :)

Regards..

So true. If the drive mounts via the GUI on the new install. That would be the best way to pull the files off it.

Hopefully it will mount and the files will be there.

---

### Post by Zac_Brazdis on 2015-10-20
Hey guys I just wanted to update this thread it turns out that the drive was actually failing as many of you suspected.

I finally got around to dropping it off at a data recovery company... they were able to recover all of the data but all the file structure and file names became renamed to random numbers but the files themselves are not corrupt and still work. I have yet to pick up my new copied external drive with my recovery files, as it will be completed later today... And I won't pick it up until lunch time tomorrow.

Now, I'm told there were a few bad sectors but they did not contain any data luckily. 

Anyway my question is, why did the file structure and file names become corrupt? This happen to me one other time when I was a young kid recovering data from Windows 3.1 as well. I forgot the specifics of how or why I did the recovery. Luckily back then 514mb of space was "a lot" of memory. So sifting through the files and renaming them was a hour job max. Regardless, I have a huge project in front of me with renaming and rebuilding the file structure of 2tb worth of data. 

Also, a good friend of mine introduced me to Kali Linux. Which I have a USB of currently in my windows 7 system with a Ubuntu partition as well. It seems to have some amazing tools which are quite powerful. But I'd like to hear from you guys on your opinion of this Linux build. It's also interesting that it can run on top of Windows instead of booting to it. It also seems to run in only 32 bit (or less!). 

Thanks in advance. Z

Oh and I do want to thank Charles and everyone else who helped me. Since then I've learned a lot about Ubuntu Linux.

---

### Post by CharlesA on 2015-10-21
The best way I could explain it would be that the file allocation tables (EXT probably calls them something different) were corrupted and that caused the original file names and directory structure to be lost. The files still existed but there was no "map" of what they belonged to or where they were.

That's kind of a simple explanation, but I hope it makes sense.

---

### Post by metafizx on 2015-12-13
> **CharlesA said:**
> That's really weird.

Here's what I get on my server (using lvm):
```

sudo fdisk -l
Disk /dev/sda: 9000.1 GB, 9000103968768 bytes
255 heads, 63 sectors/track, 1094200 cylinders, total 17578328064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
**/dev/sda1               1  4294967295  2147483647+  ee  GPT**
Partition 1 does not start on physical sector boundary.

```

```
sudo blkid -c /dev/null
/dev/sda1: UUID="rYpYn8-QFm6-flQx-Gdqv-oWkj-qUkF-Dlyek4" TYPE="LVM2_member"
/dev/mapper/Thor-Array: UUID="05c730b5-680d-4d33-8e2e-76947d7a93fa" TYPE="ext4"

```

I was able to run a fsck on that partition by running this:

```
sudo fsck -Cf UUID=05c730b5-680d-4d33-8e2e-76947d7a93fa
```

Aside from the output of your fdisk and blkid looking off, you should theoretically be able to run fsck on that device by running this:

```
sudo fsck -Cf UUID=c354b521-bcd5-494b-9679-0dc2e66b5dd6
```

thanks for all your work on this. I was able to fix my failed Seagate Central following your info.

I was able to mount the 2TB partition, but the contents were not visible. I suspect that it is some proprietary file format that Seagate must use.
However, after fixing the disk, I re-installed it into the Seagate unit, and viola ! it came up on the network and all the files were there.

_Basically to summarize the steps.._.
1. installed Xubuntu 
2. installed fuseext2
3. installed lvm2
4. sudo blkid -c /dev/null *(to get the UUID for the 2TB partition)*
5. sudo fsck -Cf UUID={replace with uuid from #4}
6. allow fsck to fix the bad blocks (answer yes to those found)
7. re-install the fixed drive into the seagate box and hopefully it works for you.

---

### Post by oldfred on 2015-12-13
I have used Photorec to recover files from a drive.
It just scans drive for anything that looks like each of the file types you have it scan for. 
It even recovered my deleted files text files, so some of them had 5 or 6 copies and I had to do a lot of work to first figure out which file was which and then compare each found file with my last backup to see which file copy had new or delete data. 

So depending on what tool they used to scan platters may be how files got named. If Photos or Music file has internal data that you can use to rename. I now include file name in all my manually created text files for same reason.

 Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local text type Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

