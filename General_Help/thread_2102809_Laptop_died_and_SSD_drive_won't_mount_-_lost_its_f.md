---
title: "Laptop died and SSD drive won't mount - lost its file system."
date: 2013-01-08
forum: General Help
---

### Post by yamagami on 2013-01-08
I have just lost my laptop (Thinkpad T61p - graphic card failure/no boot) and to add another blow I cannot  read my main SSD drive now which means I’m losing about 4-5 month worth of my life’s data.  I’m trying to recover that drive.
When the laptop died, I took out the SSD drive, put it in a USB sata encolsure, and connected it to another (olde) laptop running Ubuntu (10.04). It worked just fine and I could see my files. Later that evening I tried to use that drive to boot another similar T61p but the laptop wouldn’t boot, falling into Grub rescue mode saying there is no file system. 
I immediately reconnected it to the USB enclosure and now instead of seeing my files I get nothing. I’m pretty sure the drive was ext4 (default file system for Ubuntu 12.04).

The usual investigation produces the following:

dmesg after connecting the drive:

```
[ 1218.296064] usb 2-2: new high-speed USB device number 2 using ehci_hcd
[ 1218.460823] Initializing USB Mass Storage driver...
[ 1218.461481] usbcore: registered new interface driver usb-storage
[ 1218.461483] USB Mass Storage support registered.
[ 1218.473020] scsi5 : usb-storage 2-2:1.0
[ 1218.473104] usbcore: registered new interface driver ums-cypress
[ 1219.472848] scsi 5:0:0:0: Direct-Access        Mass  Storage Device        PQ: 0 ANSI: 0
[ 1219.473941] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 1219.475126] sd 5:0:0:0: [sdb] 195371566 512-byte logical blocks: (100 GB/93.1 GiB)
[ 1219.475561] sd 5:0:0:0: [sdb] Write Protect is off
[ 1219.475564] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 1219.476149] sd 5:0:0:0: [sdb] No Caching mode page present
[ 1219.476152] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1219.477810] sd 5:0:0:0: [sdb] No Caching mode page present
[ 1219.477812] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1219.480332]  sdb: sdb1 sdb2 < sdb5 >
[ 1219.483706] sd 5:0:0:0: [sdb] No Caching mode page present
[ 1219.483711] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 1219.483716] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 1237.936096] usb 2-2: reset high-speed USB device number 2 using ehci_hcd
```

fdisk  shows: 

```
Disk /dev/sdb: 100.0 GB, 100030241792 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371566 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c8f75

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   187117567    93557760   83  Linux
/dev/sdb2       187119614   195371007     4125697    5  Extended
/dev/sdb5       187119616   195371007     4125696   82  Linux swap / Solaris
```


sudo file -s /dev/sdb1

```
harel@yamagami:~$ sudo file -s /dev/sdb1 
/dev/sdb1: data
```


Trying to mount it:

```
harel@yamagami:~$ sudo mount -t ext4 /dev/sdb1 /mnt/damo
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg the shows this as well:

```
[ 1417.597997] EXT3-fs (sdb1): error: can't find ext3 filesystem on dev sdb1.
[ 1417.611379] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[ 1477.287884] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
```


How can I recover the drive? Should I use dd to mirror it on an image file locally and experiment with that? Is there a way to extract the data out of it? I have lost  lot there since my last backup and it would mean a lot if I could get it back.

---

### Post by oldfred on 2013-01-08
I am not sure if 10.04 supported trim or some of the settings you may have had. 

Have you tried fsck?

If booting from another drive, you do not need to use liveCD, but need to be sure to unmount before running.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by tgalati4 on 2013-01-08
Find another machine running any modern linux distro that supports ext4 and plug the drive in to verify that the data is still there.  Don't try to boot from it, just examine the file structure and use a large flash drive and start migrating your data to the flash drive.  This should have been done first, since booting on a foreign system can cause other issues, especially if the drive is starting to fail in writing data to the drive.  If you can see the file structure, then you should be able to read from it and start copying data.

Once your data is backed up, then we can try to resurrect your machine or repair the drive for booting.

How did the graphics fail?  Was it delamination of the graphics chip?

Can you hook up a vga monitor to it?

Many boot drives have a hidden (diagnostic) partition that is formatted with FAT or something else.  Are you sure your distro is located at /dev/sdb1?  Did you try /dev/sdb2 or /dev/sdb3?

---

### Post by yamagami on 2013-01-08
oldfred, are you saying that since 10.04 didn't have trim etc. simply attaching the drive to it killed it? 
I did try e2fsk on a dd image of the drive and had to keep something heavy on the enter key to approve each yes (didn't use your options though I'm getting another dd image and will do that). My result with simple vanilla e2fsk is mountable ext4 disk, without files and a LOT of entries in lost+found. Will also try testdisk...

---

### Post by yamagami on 2013-01-08
tgalati4, I did connect it to an ext4 machine afterwards though at that point the SSD was unreadable. I'm trying various methods of recovery now on a dd obtained image (from e2fsk to testdisk to photorec). Getting the back up of all or some of the data is my top priority. The drive has no other partition. I wiped it out when I put 12.04 on it a few months ago.

As for the laptop, we both went to sleep night before last, and only I woke up. When I turned it on it just gave a beep sequence that later I found out means dead graphic card. No Post, no external video, no nothing. Just sits there and starts to heat up. This has happened to me before with the same model laptop and I replaced the motherboard at the time. I will do the same to this one but as I said - hardware is just a thing. The data is emotional :)

---

### Post by tgalati4 on 2013-01-08
It sounds like the graphics chip failed, pulling down the voltage (due to heating) and that possibly caused the SSD to fail with bad writes.  More current is needed for writing than reading from an SSD.

If most of the data is intact (and it should be), testdisk should be able to resurrect the partition table and the directory structure.  If the controller on the SSD failed then it's possible that the data is damaged more extensively.

I'm using a t43p and I'm waiting for a similar failure.  I think the "p" stands for "poof".

---

### Post by yamagami on 2013-01-10
After the Graphic chip's death the SSD worked fine once attached via a usb enclosure to an old laptop running 10.04. Maybe it was its last breath... I should've backed it up at that point - serves me right. I ordered a T530 now, and although this failure has happened to me twice, I still have faith in the Thinkpad brand. Its still an old piece of hardware that worked a treat till now. Good luck with your T43p - think happy thoughts and be positive and it will outlive you :)

---

