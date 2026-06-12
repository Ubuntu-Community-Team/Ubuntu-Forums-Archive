---
title: "Trying to format an ext micro USB card but &quot;Write Protection&quot; is preventing it."
date: 2017-11-02
forum: General Help
---

### Post by p2bc on 2017-11-02
All I want to do it "dd" the Ubuntu Mate img to a micro USB card for RPi, and can't do it. I started with GParted to clean up the disk, and wipe it. Can'r because it is "write protected" for I decide to go tried and true terminal with fdisk to wipe the partitions.

I confirmed the drive:
```

sudo fdisk -l
...
Device     Boot Start    End Sectors  Size Id Type
/dev/sdc1  *     8192  49151   40960   20M  c W95 FAT32 (LBA)
/dev/sdc2       57344 581631  524288  256M 83 Linux

```


```

sudo fdisk /dev/sdc

Welcome to fdisk (util-linux 2.27.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

fdisk: cannot open /dev/sdc: **Read-only file system**

```


```

sudo blkid /dev/sdc*
/dev/sdc: PTUUID="5452574f" PTTYPE="dos"
/dev/sdc1: SEC_TYPE="msdos" UUID="18B5-D2B0" TYPE="vfat" PARTUUID="5452574f-01"
/dev/sdc2: PARTUUID="5452574f-02"

```


```

sudo hdparm -r0 /dev/sdc*

/dev/sdc:
 setting readonly to 0 (off)
 readonly      =  0 (off)

/dev/sdc1:
 setting readonly to 0 (off)
 readonly      =  0 (off)

/dev/sdc2:
 setting readonly to 0 (off)
 readonly      =  0 (off)

```

```

dmesg | tail

[275532.603421] scsi host20: usb-storage 1-1.4:1.0
[275533.729524] scsi 20:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[275533.730929] sd 20:0:0:0: Attached scsi generic sg2 type 0
[275534.398398] sd 20:0:0:0: [sdc] 30881792 512-byte logical blocks: (15.8 GB/14.7 GiB)
[275534.399487] sd 20:0:0:0: [sdc] **Write Protect is on**                                                     
[275534.399496] sd 20:0:0:0: [sdc] Mode Sense: 03 00 80 00
[275534.400632] sd 20:0:0:0: [sdc] No Caching mode page found
[275534.400649] sd 20:0:0:0: [sdc] Assuming drive cache: write through
[275534.405880]  sdc: sdc1 sdc2
[275534.409980] sd 20:0:0:0: [sdc] Attached SCSI removable disk

```


```

sudo mount -o "remount,rw" /dev/sdc1 /mnt/1
mount: /mnt/1 not mounted or bad option

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```

```

dmesg | tail
[275532.603421] scsi host20: usb-storage 1-1.4:1.0
[275533.729524] scsi 20:0:0:0: Direct-Access     Multiple Card  Reader     1.00 PQ: 0 ANSI: 0
[275533.730929] sd 20:0:0:0: Attached scsi generic sg2 type 0
[275534.398398] sd 20:0:0:0: [sdc] 30881792 512-byte logical blocks: (15.8 GB/14.7 GiB)
[275534.399487] sd 20:0:0:0: [sdc] **Write Protect is on**
[275534.399496] sd 20:0:0:0: [sdc] Mode Sense: 03 00 80 00
[275534.400632] sd 20:0:0:0: [sdc] No Caching mode page found
[275534.400649] sd 20:0:0:0: [sdc] Assuming drive cache: write through
[275534.405880]  sdc: sdc1 sdc2
[275534.409980] sd 20:0:0:0: [sdc] Attached SCSI removable disk

```

I am out of ideas. And for those wondering, I am using a micro USB adapter, and it does have a switch on the side, and I have tried it both positions with no success.

Any help in solving this conundrum would be appreciated.

---

### Post by sudodus on 2017-11-02
If you want to clone an image with 'dd' you need not clean the target drive, because the cloning process will overwrite whatever was there before (in the relevant part of the drive).

You can do it with the powerful but dangerous **dd** program, or 'wrap a safety belt around dd' with mkusb. See this link,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

If the cloning process does not work, the card might be damaged (or there might be some problem with the adapter or with the cooperation between the computer hardware or operating system and the adapter).

See this link,

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

---

### Post by Andreyshel on 2017-11-02
Some of them  have physical switch on the card itself.

---

### Post by p2bc on 2017-11-03
@**Sudodus**

It looked promising, but has been abandoned, the last update was 2016.
```

sudo add-apt-repository ppa:mkusb/ppa
Cannot add PPA: 'ppa:~mkusb/ubuntu/ppa'.
ERROR: '~mkusb' user or team does not exist.

```

@[**[COLOR=#000000]Andreyshel[/COLOR]**]("https://ubuntuforums.org/member.php?u=892028")

I know there is a physical switch, as I mentioned tried with it in both positions.


I also managed to do another disk with no problems, but when I returned  to the previous disk, the one with the errors, although all I did was  switch the disk, inserted it and hit my up arrow key once and hit  entered, it failed to copy. So it is looking more and more the disk has  been corrupted, which sucks since it is brand new.

Does anyone have any other suggestions to verify the disk. I can access  it, read from it and everything, just cannot switch the "write" mode on.  

BTW I thought I posted the fsck on the drive, apparently I did not:

```

fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdc2

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

```

At this point I am throwing every command at it, and failing
```

wipefs -a "/dev/sdc1" exited with non-zero exit status 1: wipefs: error:  /dev/sdc1: probing initialization failed: Read-only file system

```

---

### Post by sudodus on 2017-11-03
You may have been affected by a temporary error at Launchpad or somewhere in the internet.

The last update of the ppa:mkusb/ppa was made 2017-09-21. All current versions of Ubuntu and the Ubuntu community flavours can use this version (mkusb - 12.2.7-1ubuntu1). Or are you running an end of life version of Ubuntu [MATE]? Which version are you running?

[launchpad.net/~mkusb/+archive/ubuntu/ppa/+packages](https://launchpad.net/~mkusb/+archive/ubuntu/ppa/+packages)

But mkusb should work anyway with an old version (if it is not extremely old), at least if you intend to use the standard method (cloning), and not make a persistent live drive. (I should know, because I am the developer of mkusb: it consists of bash shellscripts, that use some standard programs, that belong to Ubuntu and/or can be installed from the Ubuntu repositories).

---

### Post by oldos2er on 2017-11-03
> **p2bc said:**
> @**Sudodus**

It looked promising, but has been abandoned, the last update was 2016.


I can assure you sudodus hasn't abandoned it.

---

### Post by sudodus on 2017-11-03
You can check the 'disk' (actually micro SD card) using the methods described at

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

You can check the S.M.A.R.T. information of hard disk drives and SSDs, but I don't think that micro SD cards and simple USB pendrives provide that information. You can try if you wish according to

[Scroll down to 'Maybe the disk hardware is damaged'](https://askubuntu.com/questions/948036/reformating-hard-drive-after-malware-damaged-boot-sector/948560#948560)

---

### Post by p2bc on 2017-11-08
[B]@sudodus
[/B]
Sorry for the delay in responding, I did the exact command "add repos, update, install" and this time is worked! ??? 
I ran "mkusb", and did a full wipe of the drive, it came back with no errors, or warnings. When it said it was safe to remove, I did, and re-inserted. 
Did a check, and sure enough still read-only.

Restore results:
```

sdc
Multiple_Card_Reader
14.7G
usb
USB or memory card
p_target: target=/dev/sdc
Restore  /dev/sdc 
to an MSDOS partition table and a
partition with a FAT32 file system
MODEL            NAME   FSTYPE LABEL  SIZE
Card  Reader     sdc                 14.7G
                 &#9500;&#9472;sdc1 vfat           20M
                 &#9492;&#9472;sdc2               256M
restore
/dev/sdc
testing
-----
Trying to unmount partitions if mounted on the target device
umount: /dev/sdc: not mounted
umount: /dev/sdc1: not mounted
umount: /dev/sdc2: not mounted
--------------------------------------------------------------------------------
gpt_zap: done
dd: failed to open '/dev/sdc': Read-only file system
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Error: Can't write to /dev/sdc, because it is opened read-only.
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Error: You requested a partition from 1049kB to 15.8GB (sectors 2048..30881791).
The closest location we can manage is 1049kB to 4194kB (sectors 2048..8191).
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Error: Can't write to /dev/sdc, because it is opened read-only.
mkfs.fat 3.0.28 (2015-05-16)
mkfs.vfat: unable to open /dev/sdc1: Read-only file system
 Failed :-( 
  mk_msdos: could not create MSDOS partition table and FAT file system 
Wait 5 seconds and a little more ...
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Model: Multiple Card Reader (scsi)
Disk /dev/sdc: 15.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  25.2MB  21.0MB  primary  fat16        boot, lba
 2      29.4MB  298MB   268MB   primary

 
MODEL            NAME   FSTYPE LABEL
Card  Reader     sdc           
                 &#9500;&#9472;sdc1 vfat   
                 &#9492;&#9472;sdc2  


```

Wiping results:
```

sdc
Multiple_Card_Reader
14.7G
usb
USB or memory card
p_target: target=/dev/sdc
Preparing to wipe  /dev/sdc 
MODEL            NAME   FSTYPE LABEL  SIZE
Card  Reader     sdc                 14.7G
                 &#9500;&#9472;sdc1 vfat           20M
                 &#9492;&#9472;sdc2               256M
wipe-whole-device
/dev/sdc
-----
Trying to unmount partitions if mounted on the target device
umount: /dev/sdc: not mounted
umount: /dev/sdc1: not mounted
umount: /dev/sdc2: not mounted
-------------------------------------------------------------------------------
 wipe-whole-device 
  64KiB 0:00:00 [58.9MiB/s] [>                                                                                ]  0%            
Syncing the device ...
dd: failed to open '/dev/sdc': Read-only file system
 Done, but you should also check for the line 
'dd: error writing to '/dev/sdc': No space left on device',
which means that the whole device is wiped. (Look a few lines above ^) 
Wait 5 seconds and a little more ...
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Warning: Unable to open /dev/sdc read-write (Read-only file system).  /dev/sdc has been opened read-only.
Model: Multiple Card Reader (scsi)
Disk /dev/sdc: 15.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  25.2MB  21.0MB  primary  fat16        boot, lba
 2      29.4MB  298MB   268MB   primary

 
MODEL            NAME   FSTYPE LABEL
Card  Reader     sdc           
                 &#9500;&#9472;sdc1 vfat   
                 &#9492;&#9472;sdc2        

```

---

### Post by p2bc on 2017-11-08
So I have already come to term with the fact that the drive might be damaged beyond repair, so much so I went out and bought two more cards. I am taking some positive out of all this and making it into a learning experience so I am not quite ready to give up on figuring all this out.... **BECAUSE**, wouldn't you know it I put several, I mean four plus, USB thumb drives in my USB socket, and each and every last one was deemed by _desktop_ (more about that in a second) to be read only. I formatted some, threw a few others(never said I didn't have a temper), but no matter what the _desktop_ said they were read only. I started to apply some of the things I have learned in these endeavours, particularly "dmesg | tail" where it actually said "Write protection is **OFF**". So I did a "cp ./some_file /destination" and it worked. Open Nautilus, and sure enough the "some_file" was now on the thumb drive. Tried again to drag and drop a file and still came back read only. With the Nautilus window still open from the terminal window I did "cp ,/some_other_file /destination" and sure enough I saw it pop-up in the Nautilus windows.

So something is screwy in Denmark(paraphrasing Hamlet). But I had the knowledge from this experience to to find a solution for now.

This does not explain either current problem, the SD card or the OS making read only.

As for the other two SD cards, I cloned the img off one of the original cards to the computer, then cloned the 2 new cards with no problem. So one to replace the damaged one, and one for "In Case Of"


I welcome any further thoughts on the situation.

---

### Post by sudodus on 2017-11-08
> **p2bc said:**
> ... each and every last one was deemed by _desktop_ (more about that in a second) to be read only. I formatted some, threw a few others(never said I didn't have a temper), but no matter what the _desktop_ said they were read only.

Why are you underlinining 'desktop'? Did try in another computer, and had a different result? Maybe some hardware is not compatible?
> 
I started to apply some of the things I have learned in these endeavours, particularly "dmesg | tail" where it actually said "Write protection is **OFF**". So I did a "cp ./some_file /destination" and it worked. Open Nautilus, and sure enough the "some_file" was now on the thumb drive. Tried again to drag and drop a file and still came back read only. With the Nautilus window still open from the terminal window I did "cp ,/some_other_file /destination" and sure enough I saw it pop-up in the Nautilus windows.

So something is screwy in Denmark(paraphrasing Hamlet). But I had the knowledge from this experience to to find a solution for now.

I agree that something is screwy :-P
> 
This does not explain either current problem, the SD card or the OS making read only.

As for the other two SD cards, I cloned the img off one of the original cards to the computer, then cloned the 2 new cards with no problem. So one to replace the damaged one, and one for "In Case Of"


I welcome any further thoughts on the situation.

I'm glad that you were able to clone the image file to the new cards :-)

---

### Post by p2bc on 2017-11-08
> 
Maybe some hardware is not compatible?


No, it is on my main machine that this is happening. Which I have used all these thumb drives on countless times.

Also I forgot to mention. I tried the SD card on another computer, a Mac specifically, and it could not detect it at all even with the FAT partition

---

### Post by sudodus on 2017-11-09
> **p2bc said:**
> No, it is on my main machine that this is happening. Which I have used all these thumb drives on countless times.

Also I forgot to mention. I tried the SD card on another computer, a Mac specifically, and it could not detect it at all even with the FAT partition

When you have done all this (including trying in another computer), and an SD card is read-only or not detected, I think it is beyond repair.

---

### Post by p2bc on 2017-11-09
For the SD card, on my main main machine (Ubuntu 16.04) it detects, even opens the drive, can read it and open files. Simply can not write to it because it opens in "read only" mode.
On the Mac, it does't even detect the SD card from the dedicated SD card reader slot.

---

