---
title: "xubuntu- create iso image from cd or dvd"
date: 2008-01-21
forum: General Help
---

### Post by lmart on 2008-01-21
unable to create iso from a cd or dvd

using xubuntu 7.1

tried multiple variants of the following command with no success

dd if=/dev/cdrom of=file.iso

once able to extract the iso, what is the command to write the iso to a cd or dvd?

thanks

---

### Post by smartboyathome on 2008-01-21
That should be it.

---

### Post by geirha on 2008-01-21
What does dd output when it's unsuccessful?

In ubuntu you right-click the iso and select burn to disc. Haven't used xubuntu, so I don't know if there's an equivalent there.

---

### Post by lmart on 2008-01-21
sudo su
dd if=/dev/cdrom of=file.iso

dd: opening '/dev/cdrom/': Not a directory

---

### Post by geirha on 2008-01-21
That error message indicates that you are writing ```
dd if=/dev/cdrom[color=red]/[/color] of=file.iso
```
instead of
```
dd if=/dev/cdrom of=file.iso
```

Try copy/pasting the latter.

---

### Post by lmart on 2008-01-21
thanks, however, get the same error message either way

sudo su
dd if=/dev/cdrom/ of=file.iso
dd: opening '/dev/cdrom/': Not a directory


sudo su
dd if=/dev/cdrom of=file.iso
dd: opening '/dev/cdrom/': Not a directory

---

### Post by geirha on 2008-01-21
Odd, what's the output of these commands?
```
ls -l /dev/cdrom
readlink -f /dev/cdrom
```

---

### Post by lmart on 2008-01-21
thanks for sticking with me on this one, here are the commands you requested and the system responses


ls -l /dev/cdrom
	/dev/cdrom -> hdc

readlink -f /dev/cdrom
	/dev/hdc

dd if=/dev/cdrom of=file.iso
	dd: reading '/dev/cdrom': Input/output error
	0+0 records in
	0+0 records out
	0 bytes (0 B) copied, 0.0609258 seconds, 0.0kB/s


have 4GB free disk space for a cd iso

---

### Post by geirha on 2008-01-22
> **lmart said:**
> 
dd if=/dev/cdrom of=file.iso
	dd: reading '/dev/cdrom': Input/output error
	0+0 records in
	0+0 records out
	0 bytes (0 B) copied, 0.0609258 seconds, 0.0kB/s


This would indicate that it has problems reading from your cdrom. After getting this message, type "dmesg" and see if it displays any messages regarding "hdc"

---

### Post by lmart on 2008-01-22
if you can make heads or tails out of this ... here you go, stripped out everything from the original file that referenced hdc .. appreciate your assistance ... will google dmesg to get a sense of what's going on ... tks again

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[    8.368000] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[    8.368000]     ide1: BM-DMA at 0x1428-0x142f, BIOS settings: hdc:DMA, hdd:pio
[   10.332000] hdc: SR243T, ATAPI CD/DVD-ROM drive
[   11.452000] hdc: ATAPI 24X CD-ROM drive, 128kB Cache, UDMA(33)
[  144.940000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[  144.940000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[  144.940000] ide: failed opcode was: unknown
[  144.940000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[  144.940000] end_request: I/O error, dev hdc, sector 0
[  144.940000] Buffer I/O error on device hdc, logical block 0
[  144.940000] Buffer I/O error on device hdc, logical block 1
[  144.940000] Buffer I/O error on device hdc, logical block 2
[  144.940000] Buffer I/O error on device hdc, logical block 3
[  144.944000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[  144.944000] hdc: command error: error=0x50 { LastFailedSense=0x05 }
[  144.944000] ide: failed opcode was: unknown
[  144.944000] hdc: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[  144.944000] end_request: I/O error, dev hdc, sector 0
[  144.944000] Buffer I/O error on device hdc, logical block 0

---

### Post by geirha on 2008-01-23
I certainly has some problems reading your CD. You should try a different CD, preferably one that isn't burned, to see if the problem is with the CD-drive or the CD itself. Those lines that start with "hdc: command error:" are lines you don't want to see.

---

