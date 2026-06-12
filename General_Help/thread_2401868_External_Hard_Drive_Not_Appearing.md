---
title: "External Hard Drive Not Appearing"
date: 2018-09-23
forum: General Help
---

### Post by hmorgan1979 on 2018-09-23
Hi everyone.  I have a problem that maybe you all can help with.  I am running Ubuntu Studio 18.04.  Up until yesterday morning, my Toshiba Canvio 2TB External Hard Drive was working fine.  I unhooked it from my Acer Laptop Friday afternoon because I was going to a friend's house.  When I got back Saturday morning, I hooked it back up and it didn't appear, either on my desktop or anywhere else it normally would.  When I tried manually mounting I got a "cannot read superblock" message.  I can't remember what all I tried, but will take any suggestions and post the results here if needed to help resolve this.  Thanks in advance.  I have never had this trouble before.  I have tried unhooking and reconnecting, rebooting with and without it connected, etc.  Nothing has worked.  I need this resolved because I have a lot of data on there that I need.

---

### Post by TheFu on 2018-09-23
I would wipe the disk, recreate a fresh partition table, create any new partitions needed, then restore from my backups.

I suspect this isn't useful to you at this point.  Nothing replaces having solid, known-working, backups. Nothing.

You can try running fsck on the unmounted device.  Maybe /dev/sdz1, but it is very likely this is incorrect. Use **sudo fdisk -l** to see the correct device.  If we assume /dev/sdz1 is correct (it isn't), the you'd run **sudo fsck /dev/sdz1** It might fix something.

If the disk is NTFS or FAT32, then you should use Windows to attempt corrective action, not Linux.

---

### Post by hmorgan1979 on 2018-09-24
here is what i got when i ran sudo fsck /dev/sda (my device

herman@InfernusMaximus666:~$ sudo fsck /dev/sda
[sudo] password for herman: 
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
fsck.ext2: Input/output error while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

herman@InfernusMaximus666:~$ 


I will try the suggestions it came up with and post results

herman@InfernusMaximus666:~$ sudo e2fsck -b 8193 /dev/sda
e2fsck 1.44.1 (24-Mar-2018)
e2fsck: Input/output error while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


herman@InfernusMaximus666:~$ sudo e2fsck -b 32768 /dev/sda
e2fsck 1.44.1 (24-Mar-2018)
e2fsck: Input/output error while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


that's what happened.  as stated in op, everything was working fine before i unhooked it.

---

### Post by TheFu on 2018-09-24
You need to work at the partition level, not the whole disk device.  sda is the whole disk, so that would be bad to run fsck against it.
My other post explained that, I think. Did you use **sudo fdisk -l **to get the partition table first?

---

### Post by hmorgan1979 on 2018-09-25
Here are the results of sudo fdisk -l



```
herman@InfernusMaximus666:~$ sudo fdisk -l
[sudo] password for herman: 
Disk /dev/loop0: 6.5 MiB, 6807552 bytes, 13296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 139.3 MiB, 146018304 bytes, 285192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 198.5 MiB, 208130048 bytes, 406504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 10.2 MiB, 10686464 bytes, 20872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 87.9 MiB, 92164096 bytes, 180008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 87 MiB, 91160576 bytes, 178048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 138.2 MiB, 144863232 bytes, 282936 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 199.7 MiB, 209416192 bytes, 409016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0: 29.1 GiB, 31272730624 bytes, 61079552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xd24d8f11

Device         Boot Start      End  Sectors  Size Id Type
/dev/mmcblk0p1 *     2048 61077503 61075456 29.1G 83 Linux


Disk /dev/mmcblk0boot1: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mmcblk0boot0: 4 MiB, 4194304 bytes, 8192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop8: 198.5 MiB, 208134144 bytes, 406512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 139.3 MiB, 146014208 bytes, 285184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop11: 82.2 MiB, 86147072 bytes, 168256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop12: 172.1 MiB, 180424704 bytes, 352392 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 29.7 GiB, 31914983424 bytes, 62333952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1        8192 62333951 62325760 29.7G  c W95 FAT32 (LBA)
```

Also, I am a novice at this stuff, maybe I should have mentioned that in the OP

---

### Post by TheFu on 2018-09-25
Ignore all the "loop" stuff.  Those are for the new "snap" programs. Meh.

So that leaves some MMC and sdb stuff.  I can't tell which is which, but /dev/sdb1 has a windows file system, so don't touch that with Linux.

That leaves just 1 partition, /dev/mmcblk0p1.  That's the thing you should be running fsck against. Ensure it isn't mounted at the time. If you boot from a flash drive, it should be safe.

That's what I meant when I said, > "You can try running fsck on the unmounted device. Maybe /dev/sdz1, **but it is very likely this is incorrect.** Use sudo fdisk -l to see the correct device. If we assume /dev/sdz1 is correct (**it isn't**), the you'd run sudo fsck /dev/sdz1 It might fix something."

Backups are much easier to deal with and solve 1,000 other issues, including this one.

---

### Post by hmorgan1979 on 2018-09-29
Tried what you posted.  Turns out the /dev/mmcblk0p1 is the actual laptop.  I also encountered a new wrinkle in the situation.  Either yesterday or the day before, the external showed up on my desktop, but only labeled as "Volume."  When I tried opening it I got a message reading "Could not mount; volume not found.  After a reboot (unrelated issue) it disappeared again.  Sorry for the delay in reply, life got in the way.

Ran sudo parted -l. here is the output:

```
herman@InfernusMaximus666:~$ sudo parted -l
[sudo] password for herman: 
Error: /dev/sda: unrecognised disk label
Model: TOSHIBA External USB 3.0 (scsi)                                    
Disk /dev/sda: 1695660TB
Sector size (logical/physical): 512B/16384B
Partition Table: unknown
Disk Flags: 

Model: Mass Storage Device (scsi)
Disk /dev/sdb: 31.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  31.9GB  31.9GB  primary  fat32        lba


Error: /dev/mmcblk0boot0: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/mmcblk0boot1: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: MMC HBG4e (sd/mmc)
Disk /dev/mmcblk0: 31.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.3GB  31.3GB  primary  ext4         boot

```
The Toshiba is the device I am having issues with.  I dunno if this helps better diagnose the issue.  Thanks in advance

---

### Post by wildmanne39 on 2018-12-27
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by hmorgan1979 on 2018-12-27
Sorry, but I have no idea what you mean.  I'm a noob when it comes to this stuff

---

### Post by wildmanne39 on 2018-12-27
Please see how post 6 looks now that I added code tags to the code you posted in September.

---

### Post by liaata on 2018-12-28
> **hmorgan1979 said:**
> Hi everyone.  I have a problem that maybe you all can help with.  I am running Ubuntu Studio 18.04.  Up until yesterday morning, my Toshiba Canvio 2TB External Hard Drive was working fine.  I unhooked it from my Acer Laptop Friday afternoon because I was going to a friend's house.  When I got back Saturday morning, I hooked it back up and it didn't appear, either on my desktop or anywhere else it normally would.  When I tried manually mounting I got a "cannot read superblock" message.  I can't remember what all I tried, but will take any suggestions and post the results here if needed to help resolve this.  Thanks in advance.  I have never had this trouble before.  I have tried unhooking and reconnecting, rebooting with and without it connected, etc.  Nothing has worked.  I need this resolved because I have a lot of data on there that I need.


What did you already try to fix the issue?

---

### Post by hmorgan1979 on 2019-01-01
I tried to get assistance before and it seems as though the request,  after a bit of back ad forth, never got resolved, so here goes:  I have a  Toshiba 2TB external hard drive, and an Acer Aspire laptop.  I am  currently running Ubuntu Studio 18.10.  My problem runs thusly:  about  three months or so ago, everything was fine.  My external hd was working  fine with my laptop.  One evening I had unplugged the hd from the  laptop because I was going somewhere.  I returned the next day and  hooked everything back up.  My hd doesn't show up on my desktop or in  the device list.  I have tried with a different usb cable and still  nothing.  I ran lsusb and the results are below:

```
herman@InfernusMaximus666:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 8087:07dc Intel Corp. 
Bus 001 Device 004: ID 064e:9404 Suyin Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 009: ID 0480:d011 Toshiba America Inc Canvio Desk
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


The Toshiba Canvio is the external HD.

Then I unplugged it, plugged it back in and ran  dmesg | tail -n 20.  again, results are below.
```
$ dmesg | tail -n 20
[ 6933.254573] sd 0:0:0:0: [sda] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6933.254577] sd 0:0:0:0: [sda] tag#0 Sense Key : Illegal Request [current] 
[ 6933.254580] sd 0:0:0:0: [sda] tag#0 Add. Sense: Invalid field in cdb
[ 6933.254585] sd 0:0:0:0: [sda] tag#0 CDB: Read(16) 88 00 00 00 00 00 00 00 00 04 00 00 00 04 00 00
[ 6933.254587] print_req_error: critical target error, dev sda, sector 4
[ 6933.254593] Buffer I/O error on dev sda, logical block 1, async page read
[ 6933.257004] Dev sda: unable to read RDB block 0
[ 6933.265591]  sda: unable to read partition table
[ 6933.268030] sd 0:0:0:0: [sda] Attached SCSI disk
[ 6963.946893] usb 1-2: USB disconnect, device number 11
[ 6963.950714] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 6963.950800] sd 0:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 6969.104671] usb 1-2: new high-speed USB device number 12 using xhci_hcd
[ 6969.234979] usb 1-2: New USB device found, idVendor=0480, idProduct=d011, bcdDevice= 3.16
[ 6969.234983] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 6969.234985] usb 1-2: Product: External USB 3.0
[ 6969.234987] usb 1-2: Manufacturer: TOSHIBA
[ 6969.234989] usb 1-2: SerialNumber: 20140831110664
[ 6969.238627] usb-storage 1-2:1.0: USB Mass Storage device detected
[ 6969.242967] scsi host0: usb-storage 1-2:1.0
```


Again, the Toshiba shows up. This is where everything stands at this point.
Any help would be greatly appreciated.

I tried everything that was suggested above to no avail.

---

### Post by hmorgan1979 on 2019-01-26
Is there anyone who has any suggestions?

---

### Post by tea for one on 2019-01-28
Good evening

I've had a look through this thread and there are some details that are not completely clear:-

The file system on your Toshiba external drive, is it a Linux or Windows file system?

When you "unhooked" it from your laptop, did you **safely remove** it or simply detach the cable?

It appears that you have no back-ups for this drive, is that correct?

If the file system is ext2, 3 or 4, then there is a chance that the drive can be repaired by [https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

The web link is simply a suggestion at this stage and it would be better if you could post the details of the file system on your Toshiba drive before any further action.

Best wishes

---

### Post by hmorgan1979 on 2019-02-11
First, how do I determine if it's a Windows or Linux format, second, I unhooked it while the laptop was shut off.  Yes, I have no backups, simply for the sheer amount of data on it.  Sorry for the delay in reply.  How do I determine what type of file system is on it?  All the info I could glean is already posted.Also, when I tried hooking it up to a Windows laptop, the same issue happened.  It doesn't appear anywhere.  And now it's not showing anywhere even when I run the previously working commands that had it appear before.

---

### Post by oldfred on 2019-02-11
It is seeing a sda drive, but no partition table.
And it has this error:
Invalid field in cdb

Which is related to CD/DVDs.
Did you dd copy an installer ISO to the sda drive, which converts it from a partitioned drive to a hybrid DVD drive. And then you lost partition table.

---

### Post by hmorgan1979 on 2019-02-11
No I was using it purely for storage.  No ISOs installed or anything.  I had almost 1000 movies, over 5000 songs, a bunch of pictures, ebooks, and documents on it.  I also had some install files (not ISOs) on it for morrowind and oblivion from GOG.  And when I ran sudo fdisk -l, sudo parted -l and lsusb just now it, it showed up, but won't let me run .# dumpe2fs /dev/sda | grep superblock

```
$ sudo fdisk -l
Disk /dev/mmcblk0: 29.1 GiB, 31272730624 bytes, 61079552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb4b278ec

Device         Boot Start      End  Sectors  Size Id Type
/dev/mmcblk0p1 *     2048 61077503 61075456 29.1G 83 Linux


herman@Dantes-Inferno:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label
Model: TOSHIBA External USB 3.0 (scsi)                                    
Disk /dev/sda: 1695643TB
Sector size (logical/physical): 512B/4194304B
Partition Table: unknown
Disk Flags: 

Model: MMC HBG4e (sd/mmc)
Disk /dev/mmcblk0: 31.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.3GB  31.3GB  primary  ext4         boot


Error: /dev/mmcblk0boot0: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/mmcblk0boot1: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

herman@Dantes-Inferno:~$ lsusb 
Bus 002 Device 002: ID 0480:d011 Toshiba America Inc Canvio Desk
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 8087:07dc Intel Corp. 
Bus 001 Device 005: ID 064e:9404 Suyin Corp. 
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

just tried mounting it min terminal.  I think it may be a hardware issue, because the external drive sounds like it's trying and failing to spin up.  If it's not a software issue is there any way I can recover the data or is it lost forever and i should just get a new external?  Sorry for flooding the thread but I am trying different things I had heard about as well as what I find on here.

---

### Post by oldfred on 2019-02-11
You keep using sda, drives should have partitions.
Or did you just format drive and not create partitions? Then it is a "super floppy" configuration which is not standard. Just about every tools expects partitions.

Does testdisk see drive and see any partitions?
       [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
    
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
Screenshots of several of the recovery tools
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by hmorgan1979 on 2019-02-11
I just started storing files on it out of the box.  I transferred from my old external to my new one and everything was working fine up until the time in question.  So I guess it's a superfloppy as you put it.  I don't know if it was partitioned before I started adding files but I assume not.  Is it a lost cause?

---

### Post by hmorgan1979 on 2019-02-11
Running testdisk now will post results after I get home from work

---

### Post by tea for one on 2019-02-11
> **hmorgan1979 said:**
>   And when I ran sudo fdisk -l, sudo parted -l and lsusb just now it, it showed up, but won't let me run .# dumpe2fs /dev/sda | grep superblock

Are you able to provide the error message preventing you running the command?

One more question - is your external drive attached directly to your pc or in a hub of some sort?

---

### Post by hmorgan1979 on 2019-02-11
There was no error message.  when i hit enter, nothing happened and the command line just popped up as if waiting for me to enter another command.  Also its plugged directly into the laptop, no hub.

---

### Post by tea for one on 2019-02-12
Can you attach your Toshiba drive to your laptop, identify that the drive is still **sda** run the following commands and post the output.

```
sudo dumpe2fs /dev/sda | grep superblock
```

The first command may give a reply similar to:-

> Bad magic number in super-block while trying to open /dev/sdb
Found a gpt partition table in /dev/sdb
Couldn't find valid filesystem superblock.

```
sudo dumpe2fs /dev/sda1 | grep superblock
```

The second command may provide:- 

> Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

However, if you are still trying the TestDisk route, then I would ignore my post until you have completed the TestDisk process.

In your post no. 19, you mentioned "*I just started storing files on it out of the box*", which leads me to believe that the file system is NTFS so using ext2/3/4 suggestions to establish the details of the drive will prove unsuccessful.

---

### Post by hmorgan1979 on 2019-02-16
My laptop froze as I was running g testdisk so I think im just gonna scrap the old external and get a new one to start over with.  Thanks everyone but I'm just tired of dealing with it

---

### Post by tea for one on 2019-02-17
> **hmorgan1979 said:**
> My laptop froze as I was running g testdisk so I think im just gonna scrap the old external and get a new one to start over with.  Thanks everyone but I'm just tired of dealing with it

It's unfortunate that TestDisk was unsuccessful and we were unable to help with data recovery.

Nevertheless, don't just scrap the external drive, why not try to reformat it and put it to use.

Perhaps try and use it to back up the data on your newly purchased external drive.

---

