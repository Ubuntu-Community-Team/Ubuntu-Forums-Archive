---
title: "Gparted"
date: 2015-06-09
forum: General Help
---

### Post by pfeiffep on 2015-06-09
I have a USB drive that gparted has problems with, returns this error...
error fsyncing closing devsdb: Remote IO error

I finally gave up and used Windows 7 - same machine, same USB port - partitioned and formatted (NTFS) perfectly without errors. I used a different Windows 7 machine and performed chkdsk withour any problems.
Using the same machine and USB port Ubuntu 14.04 LTS and gparted returns the same error.

I'm relatively certain that this drive is OK, and the real problem is with Ubuntu and or gparted.  

This isn't a show stopper but I'd like to use this drive as ext4.

```
sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x49a955ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    30801919    15360000    7  HPFS/NTFS/exFAT
/dev/sda3        30801920   362369071   165783576    7  HPFS/NTFS/exFAT
/dev/sda4       362371070   976771071   307200001    5  Extended
/dev/sda5       957241344   976771071     9764864   82  Linux swap / Solaris
/dev/sda6       362371072   957241343   297435136   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 40.1 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders, total 78242976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000097f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    78239743    39118848    7  HPFS/NTFS/exFAT
```


```
sudo parted -l
Model: ATA TOSHIBA MK5056GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16           diag
 2      41.9MB  15.8GB  15.7GB  primary   ntfs            boot
 3      15.8GB  186GB   170GB   primary   ntfs
 4      186GB   500GB   315GB   extended
 6      186GB   490GB   305GB   logical   ext4
 5      490GB   500GB   9999MB  logical   linux-swap(v1)


Warning: Error fsyncing/closing /dev/sdb: Remote I/O error                
Retry/Ignore? r                                                           
Warning: Error fsyncing/closing /dev/sdb: Remote I/O error                
Retry/Ignore? i                                                           
Model: SAMSUNG MP0402H (scsi)
Disk /dev/sdb: 40.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.1GB  40.1GB  primary  ntfs
```

---

### Post by sudodus on 2015-06-09
What kind of drive is it?

HDD or SSD?
IDE or SATA?
a separate 'naked' drive in a USB box or a drive that comes in a box?
What kind of USB (the drive and and the computer port) - USB 2 or 3?
What kind of USB port - built-in or a separate card or adapter?

There are many things that might not be quite compatible (maybe not strictly obeying the standard specifications). Maybe that drive works better with another computer? Maybe you have to give it up for linux and give it to someone who is running Windows.

I prefer to put a separate 'naked' drive in an eSATA and USB (3) box.

---

### Post by pfeiffep on 2015-06-09
Thanks for you reply sudodus. This is a Firelite smartdisk usb 2 HDD accessed from USB buitlin on both HP and Dell.
I used this drive with an older Dell and had Ubuntu 12/04 installed and it booted perfectly. 

From my original post:
> Model: SAMSUNG MP0402H (scsi)
Disk /dev/sdb: 40.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.1GB  40.1GB  primary  ntfs


> 
*-usb:1
       description: Mass storage device
       product: FireLite (USB 2.0)
       vendor: SMARTDISK Corp.
       physical id: 6
       bus info: usb@2:6
       logical name: scsi12
       version: 0.00
       serial: SDC0000303
       capabilities: usb-2.00 scsi emulated scsi-host
       configuration: driver=usb-storage maxpower=2mA speed=480Mbit/s
     *-disk
          description: SCSI Disk
          physical id: 0.0.0
          bus info: scsi@12:0.0.0
          logical name: /dev/sdh
          size: 37GiB (40GB)
          capabilities: partitioned partitioned:dos
          configuration: logicalsectorsize=512 sectorsize=512 signature=000097f5

---

### Post by mc4man on 2015-06-09
What kernel? & if  at or higher than 3.13.0-35 do you have the means to try an earlier kernel?
While the reported message is different seems similar to this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1366538](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1366538)

---

### Post by pfeiffep on 2015-06-09
Thanks mc4man, I'll download 12.04 and try with that. I think the bug you referenced is very similar to what I'm experiencing.

---

### Post by pfeiffep on 2015-06-09
Using Ubuntu 12.04.5,  Kernel 3.13.0-32 the drive works perfectly, same exact hardware. I'm positive that the problem is either gparted or the Kernel for 14.04.2

---

### Post by mc4man on 2015-06-10
you probably can get an earlier 3.13 from 14.04 repos, usually 3 packages or so, or if doing a 14.04 new install then use either the 14.04 or 14.04.1 image from here. 14.04 has 3.13.0.24, 14.04.1 has 3.13.0-32, I'd try 14.01
[http://old-releases.ubuntu.com/releases/14.04.0/](http://old-releases.ubuntu.com/releases/14.04.0/)

---

### Post by pfeiffep on 2015-06-10
Thanks mc4man, I think I'll use this drive as a backup OS and keep 12.04.5 installed on it for the unusual case I need to test an older kernel.
I have reported a bug with gparted 0.18.0 and ubuntu 14.04.2

---

### Post by pfeiffep on 2015-06-11
Bug reported also occurs with vivid
#[lpbug]1464060[/lpbug]

---

### Post by LastDino on 2015-06-11
> **pfeiffep said:**
> Bug reported also occurs with vivid
#1464060

Out of curiosity, have you tried with other partition managers? I mean, you can use something like gdisk to check out if it is just gparted or the new kernel. It will help pin pointing the issue.

---

### Post by pfeiffep on 2015-06-11
Thanks Lastdino for the response and suggestion
I did not use another linux partion manager. I'll gladly try gdisk to see if the a similar error is reported. 
In summary there are 2 kernels affected with 2 gparted versions
Windows 7 reports all ok
Ubuntu 12.04.5 reports all ok
Ubuntu 14.04.2 reports a problem
Ubuntu 15.04 reports a problem

---

### Post by pfeiffep on 2015-06-11
Well now, I'm a complete novice with gdisk ... here are commands I used after reading the man page ... I don't want to write anything to the disk with vivid or trusty

I think this is indicative of a working drive and the problem is with either gparted 0.19.0 or vivid. 

```
pfeiffep@pete-HP:~$ uname -r
3.19.0-18-generic
pfeiffep@pete-HP:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

pfeiffep@pete-HP:~$ sudo gdisk -l /dev/sdh
[sudo] password for pfeiffep: 
GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sdh: 78242976 sectors, 37.3 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 460F1C67-51D0-4BB6-92EA-2C8B8EA62128
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 78242942
Partitions will be aligned on 1-sector boundaries
Total free space is 117909 sectors (57.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63        78125062   37.3 GiB    8300  Linux filesystem
pfeiffep@pete-HP:~$ sudo gdisk -p /dev/sdh
GPT fdisk (gdisk) version 0.8.10
```

---

### Post by jacques6 on 2015-12-19
Hi All,

This is a lot later, but hopefully it will help someone else. I am using 
$ uname -r
3.16.0-55-generic
uname -a
Linux ubuntu 3.16.0-55-generic #74~14.04.1-Ubuntu SMP Tue Nov 17 10:15:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


$ dpkg -l | grep gpart
ii  gparted                                               0.18.0-1                                            amd64        GNOME partition editor

I had an issue with these sync I/O errors with a 8GB uSD card the other day, and funny thing, today with a USB 300GB drive too. With the uSD, I am using ubuntu 14.04.1, with gparted 0.18, so I repartitioned the uSD card in my Centos machine at work, unfortunately, i don't know what version of gparted i'm using there.

Using gdisk as mentioned above, all worked fine on the 300GB today, on my Ubuntu 14 laptop (the one with gparted 0.18 installed on it).

Everything would point to gparted being the culprit.

Does anyone know if or when a fix will be provided?

Regards


> **pfeiffep said:**
> Well now, I'm a complete novice with gdisk ... here are commands I used after reading the man page ... I don't want to write anything to the disk with vivid or trusty

I think this is indicative of a working drive and the problem is with either gparted 0.19.0 or vivid. 

```
pfeiffep@pete-HP:~$ uname -r
3.19.0-18-generic
pfeiffep@pete-HP:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

pfeiffep@pete-HP:~$ sudo gdisk -l /dev/sdh
[sudo] password for pfeiffep: 
GPT fdisk (gdisk) version 0.8.10

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************

Disk /dev/sdh: 78242976 sectors, 37.3 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 460F1C67-51D0-4BB6-92EA-2C8B8EA62128
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 78242942
Partitions will be aligned on 1-sector boundaries
Total free space is 117909 sectors (57.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63        78125062   37.3 GiB    8300  Linux filesystem
pfeiffep@pete-HP:~$ sudo gdisk -p /dev/sdh
GPT fdisk (gdisk) version 0.8.10
```

---

