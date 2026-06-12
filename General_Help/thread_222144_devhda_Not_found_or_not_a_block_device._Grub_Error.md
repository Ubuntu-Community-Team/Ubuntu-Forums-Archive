---
title: "/dev/hda: Not found or not a block device. Grub Error"
date: 2006-07-24
forum: General Help
---

### Post by ironfistchamp on 2006-07-24
Hey I amt rying to reinstall Grub. I booted from the live CD, mounted the Ubuntu Partition, chrooted to it and type grub-install /dev/hda (primary drive).

I get the error 

/dev/hda: Not found or not a block device.

Can anyone help?

Thanks

Ironfistchamp

---

### Post by Paerez on 2006-07-24
can you run this for me:
```
ln -sf /dev/hd*
ln -sf /dev/sd*
```
and paste it for me. Also can you post:
```
cat /etc/fstab
```

---

### Post by ironfistchamp on 2006-07-24
the output was 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               reiserfs notail          0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda1       /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


Thats all I got.

Thanks

Ironfistchamp

---

### Post by Paerez on 2006-07-24
then your command is correct:
```
sudo grub-install /dev/hda
```
you can also try this:
```
grub
```
then at the grub prompt type:
```
root (hd1,0)
setup (hd0)
quit
```
root (hd1,0) means that linux is at hdb1 and setup hd0 means to write to the mba (same as grub-install /dev/hda).

---

### Post by ironfistchamp on 2006-07-24
This is the output I got

    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd1,0)

Error 21: Selected disk does not exist

grub> setup (hd0)

Error 12: Invalid device requested

grub> quit


Any other ideas?

Thanks

---

### Post by Paerez on 2006-07-24
that's really weird. How about the output of:
```
dmesg | grep 'hd'
```

---

### Post by ironfistchamp on 2006-07-24
Here we go

```
[4294674.111000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:DMA
[4294674.111000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:DMA, hdd:DMA
[4294674.375000] hda: ST380011A, ATA DISK drive
[4294674.630000] hdb: ST380011A, ATA DISK drive
[4294675.361000] hdc: _NEC DVD_RW ND-3540A, ATAPI CD/DVD-ROM drive
[4294675.984000] hda: max request size: 1024KiB
[4294675.994000] hda: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294675.995000] hda: cache flushes supported
[4294675.995000]  hda: hda1 hda2
[4294675.998000] hdb: max request size: 1024KiB
[4294675.998000] hdb: Host Protected Area detected.
[4294675.998000] hdb: Host Protected Area disabled.
[4294675.998000] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[4294675.998000] hdb: cache flushes supported
[4294675.998000]  hdb: hdb1 hdb2
[4294676.029000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294678.851000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294678.851000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294678.851000] end_request: I/O error, dev hdc, sector 1429192
[4294678.851000] Buffer I/O error on device hdc, logical block 357298
[4294679.583000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294679.583000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294679.583000] end_request: I/O error, dev hdc, sector 1429192
[4294679.583000] Buffer I/O error on device hdc, logical block 357298
[4294680.400000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294680.400000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294680.400000] end_request: I/O error, dev hdc, sector 1429192
[4294680.400000] Buffer I/O error on device hdc, logical block 357298
[4294680.931000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294680.931000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294680.931000] end_request: I/O error, dev hdc, sector 1429192
[4294680.931000] Buffer I/O error on device hdc, logical block 357298
[4294681.461000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294681.461000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294681.461000] end_request: I/O error, dev hdc, sector 1429192
[4294681.461000] Buffer I/O error on device hdc, logical block 357298
[4294681.992000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294681.992000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294681.992000] end_request: I/O error, dev hdc, sector 1429192
[4294681.992000] Buffer I/O error on device hdc, logical block 357298
[4294787.721000] Adding 2843496k swap on /dev/hdb2.  Priority:-1 extents:1 across:2843496k
[4294877.098000] ReiserFS: hdb1: found reiserfs format "3.6" with standard journal
[4294881.519000] ReiserFS: hdb1: using ordered data mode
[4294881.543000] ReiserFS: hdb1: journal params: device hdb1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[4294881.544000] ReiserFS: hdb1: checking transaction log (hdb1)
[4294881.578000] ReiserFS: hdb1: Using r5 hash to sort names

```

---

### Post by Paerez on 2006-07-24
ok you stumped me. I really have no clue why it won't install to your MBR, sorry...

---

### Post by ironfistchamp on 2006-07-24
Damn maybe it's time to reinstall ubuntu again. What is this second time in a day. It's turning into XP :o

Thanks for your help though

Ironfistchamp

---

### Post by Paerez on 2006-07-24
funky hardware is the bane of linux...

you're welcome, for what I could do, which wasn't anything :-/

---

### Post by Tintagel on 2006-07-25
> **ironfistchamp said:**
> This is the output I got

    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root (hd1,0)

Error 21: Selected disk does not exist

grub> setup (hd0)

Error 12: Invalid device requested

grub> quit


Any other ideas?

Thanks
I think you should have typed;

root (hd0,1)
setup (hd0)
quit

---

### Post by Paerez on 2006-07-25
if you look at his fstab, hda2 is his /home and hdb1 is his /. so "root (hd0,1)" would tell grub to find a kernel in his /home.

---

### Post by dranger003 on 2006-07-25
Hi guys, /dev/hda & /dev/hdb1 do not exist because of udev (which makes the devices in /dev dynamically appear upon booting the OS).

Here's what you need to do - Boot with the Ubuntu Live CD and open a Terminal then type this:

sudo mount /dev/hdb1 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt
grub-install /dev/hda
Ctrl+D
Ctrl+D
Reboot

For more info, read this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf0ad184b84304b51996a11111a1901667529a80](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf0ad184b84304b51996a11111a1901667529a80)

---

### Post by ironfistchamp on 2006-07-25
Thanks for the replies. I reinstalled Ubuntu to fix it. I had only had that install a couple of hours so it didn't matter I hadn't done anything to it. 

It is weird though because the hundreds of other times I had done it I had no problems like this and everything went off without a hitch.

Thanks

Ironfistchamp

---

