---
title: "DVD-burning: every second DVD ruined"
date: 2006-11-29
forum: General Help
---

### Post by felixj on 2006-11-29
Hi.
Strange problem over here. I need to copy a dvd so times, so I made an iso-image und burn that an dvds. Works nicely except:
I burn one DVD - works
I burn second DVD - screwed up
I burn third DVD - works again
and so on.

This happens in gnome-baker, serpentine & k3b. Any possible explanations? Where are the log-files I could post here? Is there some kind of cache that I should empty before starting a fresh burn? How do I do that?

thanks,
felixj

---

### Post by mgmiller on 2006-11-29
Don't use the burning apps you have been trying.  Ubuntu supports direct iso writing.  Just right click the .iso file and select write to disc.  I use that a lot and have no problems at all.

---

### Post by felixj on 2006-11-30
As far as I know serpentine starts up when you right-click on the iso file and select "burn to disc". I already did that with the result described above. 

thanks anyway,
felixj

---

### Post by viciouslime on 2006-11-30
This is a really weird problem, if you do find the solution elsewhere please post back here!

Meanwhile have your tried nautilus' built in ISO burning feature, as mentioned above?

---

### Post by felixj on 2006-11-30
yes, i did use the nautilus burning tool. same problem.

---

### Post by felixj on 2006-11-30
OK, I found some stuff out:

dmesg output after failed write:
```

[17181164.096000] hdd: DMA timeout retry
[17181164.096000] hdd: timeout waiting for DMA
[17181169.384000] hdd: status timeout: status=0xd0 { Busy }
[17181169.384000] ide: failed opcode was: unknown
[17181169.384000] hdd: drive not ready for command
[17181169.432000] hdd: ATAPI reset complete

```

DMA is enabled. These are the normal settings for my dvdwriter:
```

sudo hdparm /dev/hdd

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```


Interesstingly,  the settings are altered after a failed burn. The IO_support is set back to "0", 16-bit support: 
```

sudo hdparm /dev/hdd

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

When I manually alter the io-settings before the next burn, doing an
```

sudo hdparm -c1 /dev/hdd

```
the next write works nicely (but it also did that before I realized the IO-settings were changed).

I wonder if this has to do with the 
```

 HDIO_GETGEO failed: Inappropriate ioctl for device

```
error that hdparm spits out. I did some googling on that, but couldn't get any answers. 


felixj

---

### Post by felixj on 2006-11-30
More news. A post on the fa.linux.kernel ([http://groups.google.sk/group/fa.linux.kernel/msg/a8d8d1bae2e550bc](http://groups.google.sk/group/fa.linux.kernel/msg/a8d8d1bae2e550bc)) group suggested that the problem might be related to the drive not being shut down after the write by the kernel.
This is what my dmesg-output said after failed writes:
```
[17181169.384000] hdd: status timeout: status=0xd0 { Busy }
```
So I checked the drive after a succesful write with:
```
sudo hdparm -C /dev/hdd
Password:

/dev/hdd:
 drive state is:  active/idle
```
Indeed, the drive was still active, although no disc whatsoever was in it. So I shut the drive down with
```
sudo hdparm -Y /dev/hdd

/dev/hdd:
 issuing sleep command
```
Which resulted in the following dmesg-output:
```
[17184015.408000] hdd: status error: status=0x50 { DriveReady SeekComplete }
[17184015.408000] ide: failed opcode was: unknown
[17184015.408000] hdd: status error: status=0x50 { DriveReady SeekComplete }
[17184015.408000] ide: failed opcode was: unknown
[17184015.408000] hdd: status error: status=0x50 { DriveReady SeekComplete }
[17184015.408000] ide: failed opcode was: unknown
[17184015.408000] hdd: status error: status=0x50 { DriveReady SeekComplete }
[17184015.408000] ide: failed opcode was: unknown
[17184015.408000] hdd: DMA disabled
[17184015.456000] hdd: ATAPI reset complete
```
So now the kernel turned off DMA-support. Indeed:
```
sudo hdparm /dev/hdd 

/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
```
So I turned DMA back on
```
sudo hdparm -d1 /dev/hdd

/dev/hdd:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)
```

Now I tried another write with the nautilus burning tool: It works. 
So now I can do several consecutive writes, but have to issue the commands
hdparm -Y /dev/hdd
hdparm -d1 /dev/hdd
inbetween, which gets on my nerves.

If anybody has an idea for this fascinating problem, shoot.

felixj.

---

### Post by gosh on 2006-12-09
Have you find anything on this yet?
I have the same problem.

When booting it says 10 times:

```
hdd: drive not ready for command
```

dmesg:
```
$ dmesg | grep hdd
[   22.781526]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:DMA, hdd:DMA
[   24.657970] hdd: PHILIPS DVDR1648P1, ATAPI CD/DVD-ROM drive
[   29.848605] hdd: status timeout: status=0xd0 { Busy }
[   29.852208] hdd: ATAPI CD-ROM drive, 0kB Cache, UDMA(33)
[   34.847470] hdd: status timeout: status=0xd0 { Busy }
[   34.847481] hdd: drive not ready for command
[   39.846337] hdd: status timeout: status=0xd0 { Busy }
[   39.846350] hdd: drive not ready for command
[   44.921124] hdd: status timeout: status=0xd0 { Busy }
[   44.921137] hdd: drive not ready for command
[   50.031877] hdd: status timeout: status=0xd0 { Busy }
[   50.031890] hdd: drive not ready for command
[   55.030740] hdd: status timeout: status=0xd0 { Busy }
[   55.030753] hdd: drive not ready for command
[   60.029608] hdd: status timeout: status=0xd0 { Busy }
[   60.029620] hdd: drive not ready for command
[   65.036464] hdd: status timeout: status=0xd0 { Busy }
[   65.036477] hdd: drive not ready for command
[   70.067298] hdd: status timeout: status=0xd0 { Busy }
[   70.067310] hdd: drive not ready for command
[   75.070160] hdd: status timeout: status=0xd0 { Busy }
[   75.070173] hdd: drive not ready for command
[   85.183774] hdd: status timeout: status=0xd0 { Busy }
[   85.183787] hdd: drive not ready for command
[   90.226594] hdd: status timeout: status=0xd0 { Busy }
[   90.226606] hdd: drive not ready for command
[  122.641304] hdd: status timeout: status=0xd0 { Busy }
[  122.641318] hdd: drive not ready for command
[  127.640169] hdd: status timeout: status=0xd0 { Busy }
[  127.640182] hdd: drive not ready for command
[  132.643030] hdd: status timeout: status=0xd0 { Busy }
[  132.643044] hdd: drive not ready for command
[ 1441.039217] hdd: status timeout: status=0xd0 { Busy }
[ 1441.039231] hdd: drive not ready for command
[ 1668.569527] hdd: status timeout: status=0xd0 { Busy }
[ 1668.569541] hdd: drive not ready for command

```

hdparm:
```
$ sudo hdparm /dev/hdd

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

---

### Post by Spookcow on 2007-12-30
I've got the same prob! Wish there was a fix

---

