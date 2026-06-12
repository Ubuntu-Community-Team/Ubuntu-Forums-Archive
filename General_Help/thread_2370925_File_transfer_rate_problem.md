---
title: "File transfer rate problem"
date: 2017-09-08
forum: General Help
---

### Post by Lambertus on 2017-09-08
I cannot reload large numbers of files from an external drive to the computer hard drive anymore. Why?

The file transfer rate deteriorates quickly as files are copied. The rate starts at 30MB/s and decreases quickly to 0.6MB/s and lower. Does not matter if cp, rsync, or nautilus copy and paste are used. Experiments show that it seems to be a combination of the number of files and total size of copy. For example after two days of continuous copy 250 GB of data files were still not copied from a 500GB external hard drive through a USB2.0 connection to a 1TB internal drive. 
Rebooting computer resets the transfer rate to 30MB/s. Once stuck at 1MB/s or less, any transfer after that is that slow or slower.

Below are results of some experiments and the computer configurations.
After a small copy of a few files less than 8 GB started at 30MB/s and ended at 15MB/s, another copy was started through copy and paste with Nautilus so I could track what was copied and the rates.

2,031 items of 10.7 GB.
 Transfer rate first increased from 15MB/s to 27MB/s.  
After 7 GB were copied the transfer rate reduced quickly again. 
By the time 7.4GB were copied the rate was at 13 MB/s and still dropping.  
0825 items;07.8GB;08.0MB/s 
0825 items;07.8GB;07.8MB/s
0825 items;08.0GB;07.0MB/s 
0825 items;08.2GB;06.0MB/s 
0825 items;08.5GB;05.0MB/s
2031 items;10.7GB;04.0MB/s

Started next transfer right away: 27 items of 20.9GB
0001 items;01.0GB;29.0MB/s
0004 items;03.4GB;25.0GB/s
0010 items;06.8GB;26.3GB/s
0010 items;06.8GB;26.3GB/s
0010 items;08.9GB;27.0GB/s
0012 items;12.4GB;27.9GB/s
0016 items;15.6GB;28.5GB/s
0026 items;18.5GB;28.9GB/s
0026 items;20.5GB;27.7GB/s

so maybe it is number of files and not amount of GB?

Started next transfer right away: 73 items of 40.3GB
0010 items;00.5GB;24.0MB/s
0030 items;00.9GB;10.0MB/s
0032 items;01.0GB;06.0MB/s
0034 items;01.1GB;04.7MB/s
0036 items;01.1GB;04.0MB/s
0036 items;01.2GB;03.0MB/s ("approximately 4 hours left")
0036 items;01.8GB;02.0MB/s ("approximately 5 hours left")
killed the process

Restarted copy of the last file in above series: 1 file of 4.3GB
0000 items;00.0GB;01.0MB/s
killed the process and closed Nautilus

Restarted Nautilus after 1 minute and started copy of the last file in above series: 1 file of 4.3GB
0000 items;00.0GB;0.8MB/s
killed the process and closed Nautilus at 10:56 left computer running

Restarted Nautilus after 2 hours
4 items of 3.5GB
0000 items;00.0GB;0.7MB/s
Killed the process, closed Nautilus and rebooted computer

reconnected 2TB external drive and restarted Nautilus
4 items of 3.5GB
0003 items;01.8GB;30.0MB/s

started new copy
15 items at 12.6GB
0006 items;02.3GB;30.6MB/s
0010 items;04.8GB;24.0MB/s (now copying 4.3GB file)
0010 items;05.1GB;20.0MB/s
0010 items;05.3GB;17.0MB/s
0010 items;05.3GB;15.0MB/s
0010 items;05.3GB;13.0MB/s
0010 items;05.4GB;10.0MB/s
0010 items;05.6GB;08.0MB/s
0010 items;05.7GB;07.0MB/s
0010 items;05.8GB;06.0MB/s
0010 items;06.0GB;05.0MB/s
0010 items;06.3GB;04.0MB/s
0010 items;06.9GB;03.0MB/s
killed the process and restarted Nautilus

restarted Nautilus and copied a 4.3GB file
0000 items;00.0GB;29.0MB/s
0000 items;00.8GB;18.0MB/s
0000 items;01.0GB;08.3MB/s
0000 items;01.1GB;05.3MB/s
killed the process, closed all programs and rebooted the computer

Reconnected the Seagate 2tb external drive, opened Nautilus windows and gedit.
Started copy of same 4.3 GB file above.
0000 items;00.0GB;30.0MB/s
0000 items;04.0GB;30.7MB/s
0001 items;04.3GB;30.7MB/s



 My System.
Ubuntu 17.04 32-bit installed as of September 3, 2017
ASUS MSA99X EVO 2.0 motherboard
AMD FX(tm)-8320 Eight-Core Processor × 8
RAM 16MB 
XFX R7850 Graphics Card (Gallium 0.4 on AMD PITCAIRN (DRM 2.49.0 / 4.10.0-33-generic, LLVM 4.0.0))
Audigy2 Soundblaster Audio card (Linux does not understand the on-board audio)
Seagate Barracuda 1TB internal hard drive with OS and primary files (sata)
Seagate 500GB external hard drive with USB 2.0 connector
Seagate 2TB expansion external hard drive with sata to usb connector

---

### Post by HermanAB on 2017-09-09
Sounds like it is time to run fsck at boot up.

---

### Post by Lambertus on 2017-09-09
> **HermanAB said:**
> Sounds like it is time to run fsck at boot up.

Ran fsck on internal boot drive (1TB) through live DVD. Result: "clean" and listing of bytes on board.

Rebooted.
Phenomenon still happening.

It's like a copy cache gets filled up.
RAM use shows no change
CPU loads stay constant and at a minimum
Mobo port feature conficts? sata? usb?

---

### Post by Lambertus on 2017-09-10
Update.

Have now used the USB 3.0 port to load files (Seagate 2TB can do USB 3).
Turned off power saving function (board has a power save switch).
Result is essentially the same.
Could copy 31.8GB at 115MB/s before rapid transfer rate degradation (rapidly dropped to 10 MB/s)
Stopped process, rebooted and that resets the transfer speed to 115 MB/s (still pathetic for USB 3 and the drives. Copies for awhile at 115MB/s, and then rate drops quickly.
Anomalously, a couple days ago, the copy started at 1GB/s and quickly dropped to 10 MB/s over 8 GB of copy.

---

### Post by papibe on 2017-09-10
Hi Lambertus.

Could you run these commands with all disks connected, and post back the results?
```
df -hlT

df -ihlT
```
Could you also identify your source and destination disks from that output?

Regards.

---

### Post by mc4man on 2017-09-10
> **Lambertus said:**
> 
Anomalously, a couple days ago, the copy started at [COLOR="#FF0000"]1GB/s[/COLOR] and quickly dropped to 10 MB/s over 8 GB of copy.
Not possible thru any usb inc. 3.1+
Slowdowns thru extended writes is expected (maybe not to your extent), but overall there are too many variables to make any general est. of speeds.
Rather than list maybe take quick read of these 2 articles, there are many more around.

[https://blog.startech.com/post/all-you-need-to-know-about-uasp/](https://blog.startech.com/post/all-you-need-to-know-about-uasp/)
[https://www.everythingusb.com/speed.html](https://www.everythingusb.com/speed.html)

Best performance for usb would be with both devices usb3.1 or 3.1+ (uasp supported matters, real world superspeed+ is usually a pipe dream..), usb3 ssd drive (a real drive, not thumb) & probably on win10 vs. linux
Here with a adata usb3 ssd (mid range performer) & a 4+ yr old lenovo laptop (usb3 ss, no uasp) I average between 120 -180 MB/s depending on what's being transferred. (large #of small files is slower than small # of large files
,

---

### Post by HermanAB on 2017-09-11
BTW, 10 MB/s sustained write is actually quite fast - a class 10 device.  Most solid state devices are very slow when writing.

[http://www.expertreviews.co.uk/storage/1404380/how-to-choose-an-sd-card-class-and-speed-ratings-explained-and-pick-the-best-microsd](http://www.expertreviews.co.uk/storage/1404380/how-to-choose-an-sd-card-class-and-speed-ratings-explained-and-pick-the-best-microsd)

---

### Post by BenginM on 2017-09-11
Hiya Lambertus , 

Doy you experience the same slowness moving  files between partitions on the same disk and copying between local  directory to another, or in network transfers ?
Do you notice CPU activity maxed out with I/O wait time. it could be kernel default I/O scheduler, CFQ issue!

Which kernel base is currently in use while transferring files ?

I  also experience slowness while copying larg files from external disk  using thunar , but somehow cp in terminal is much faster, So i use that.

transfer files ,  in a terminal run:

$ dmesg | tail -50

Any disk-related messages? like read errors and IO waits!

Have you Checked that SATA cables are fully inserted, and not loose!


Also, check the discs SMART status. You can use disc utility for this or smartctrl

$ sudo apt install smartmontools
Perform an extended test. 

while the external disks plugged in , run $ mount 

is the flag sync set in the mount point line for those external disks, it shouldn't be set as it forces a greater amount of writing  operating on the drive. This makes the writing speed considerably lower  and also leads to a faster wear out of the disk.

 the line you're looking for , for instance on my system:

```

/dev/sdb1  on /media/sary/MYPASSPORT type vfat  (rw,nosuid,nodev,relatime,uid=1000,gid=1000,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)

```

Also, what do get from
$ sudo hdparm -tT /dev/sda
$ sudo hdparm -tT /dev/sdb , if sdb is the external disk device.

if you open disk utility , Go to drive settings and set write cache on both internal and external disks , try transferring files .. does that increase transfer speed !

I've just set write cache ON on both internal and external HDD and transfered 18GB files to the HDD with the speed of 25.8 MB/sec using thunar file manager , you may have a better result with an SSD.

Also, Do you care to share the brand of these disks and the files system format on em'! and external disks connected directly to the ports and not using a USB hub, Right?

---

