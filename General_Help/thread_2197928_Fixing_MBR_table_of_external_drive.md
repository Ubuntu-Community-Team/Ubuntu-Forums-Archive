---
title: "Fixing MBR table of external drive"
date: 2014-01-06
forum: General Help
---

### Post by gerwalt on 2014-01-06
After I messed up the GPT table of my main harddrive, some tools told me my 1TB external drive has actually 2TB. So I used gparted to extend the partition. I checked the hard drive and everything seemed fine. But when I wrote something to it, the harddrive became inaccessible. I assume the harddrive has actually only 1TB (the harddisk is in a case, so I cant check the label).

I already tried to rewrite the MBR of the external drive, but I'm not sure, what the correct number of sectors might be for start, end and size.

fdisk output for that drive:

```
$ sudo fdisk -l /dev/sde


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  1953525166   976762552    7  HPFS/NTFS/exFAT
```

parted output for that drive:

```
$ sudo parted /dev/sde unit s printModel: WD 10EACS External (scsi)
Disk /dev/sde: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End          Size         Type     File system  Flags
 1      63s    1953525166s  1953525104s  primary
```

Output of dmesg when attaching that drive:

```
[ 7792.905572] usb 1-1.2: new high-speed USB device number 5 using ehci-pci
[ 7792.998930] usb 1-1.2: New USB device found, idVendor=1058, idProduct=1100
[ 7792.998932] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 7792.998934] usb 1-1.2: Product: My Book         
[ 7792.998935] usb 1-1.2: Manufacturer: Western Digital 
[ 7792.998936] usb 1-1.2: SerialNumber: 57442D574341534A30393431333733
[ 7792.999363] scsi7 : usb-storage 1-1.2:1.0
[ 7793.998087] scsi 7:0:0:0: Direct-Access     WD       10EACS External  1.65 PQ: 0 ANSI: 4
[ 7793.999008] sd 7:0:0:0: Attached scsi generic sg5 type 0
[ 7794.001221] sd 7:0:0:0: [sde] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[ 7794.002257] sd 7:0:0:0: [sde] Write Protect is off
[ 7794.002262] sd 7:0:0:0: [sde] Mode Sense: 21 00 00 00
[ 7794.003385] sd 7:0:0:0: [sde] No Caching mode page found
[ 7794.003388] sd 7:0:0:0: [sde] Assuming drive cache: write through
[ 7794.006132] sd 7:0:0:0: [sde] No Caching mode page found
[ 7794.006136] sd 7:0:0:0: [sde] Assuming drive cache: write through
[ 7794.023054]  sde: sde1
[ 7794.026132] sd 7:0:0:0: [sde] No Caching mode page found
[ 7794.026137] sd 7:0:0:0: [sde] Assuming drive cache: write through
[ 7794.026141] sd 7:0:0:0: [sde] Attached SCSI disk
```

---

### Post by YesWeCan on 2014-01-06
The external drive has a single NTFS partition. You may want to use Windows to do a filesystem check.
What application reported it as 2TB?

---

### Post by gerwalt on 2014-01-06
Yes, single NTFS partition. Will check it with windows.

testdisk, fdisk, gparted. But since I resized it with GParted and afterwards rewrote its MBR manually it only shows 1TB

---

### Post by gerwalt on 2014-01-06
Windows recognizes the drive, but only as a RAW drive on which chkdsk isnt able to run. I will give it a try at Sevenforums.

---

### Post by YesWeCan on 2014-01-06
[http://www.sevenforums.com/](http://www.sevenforums.com/)
When it comes to Windows stuff this is a very good website.

I am curious as to how GParted was able to expand the partition to 2TB on a 1TB disk. That's very odd. Especially as fdisk is reporting the disk as 1TB
 which is correct. GParted would have to *think* the disk 2TB - it would be interesting to know how that happened in case there is a problem that needs
reporting.

Good luck. This should be much easier to fix than your SSD.

---

### Post by gerwalt on 2014-01-06
Well, I dont have it fixed yet, but they are already helping... At least I've learned a lot the last 3 days and definitely this will not happen again to me ^^

To your question:
fdisk and bootinfoscript (should see that in the other post about the GPT drive) reported the disk to be 2TB as well before I mangled it. So this is definitely not a GParted bug or mistake. I assume that the drive was already delivered with the wrong drive size by the manufacturer. I never recognized that, because I never formatted or resized it and I already own it for more than 6 years.

---

### Post by gerwalt on 2014-01-07
I didn't got the MBR fixed, but If anyone has a similar problem with an NTFS he could use Partition Wizard by MiniTool or Power Data Recovery by MiniTool, although the latter has a limit to 1GB to recover data in the free edition.

---

### Post by gerwalt on 2014-01-08
Well I got the MBR fixed in the end.

Used ntfsfix, which fixed the sector count, but couldnt work with the MFT.

```
$ sudo ntfsfix /dev/sda1
```

(You have to replace "/dev/sda1" with your device.)

After that I could still not mount the drive in Windows, but I could use chkdsk which could repair the MFT.

---

