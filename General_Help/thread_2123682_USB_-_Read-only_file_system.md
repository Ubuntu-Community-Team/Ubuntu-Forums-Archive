---
title: "USB - Read-only file system"
date: 2013-03-08
forum: General Help
---

### Post by tigy888 on 2013-03-08
I have a Buffalo 32GB USB 3.0 flash drive which suddenly became a "Read-only file system".
Thus, I can't read nor write files onto the USB. When checking permissions I got the following:

Owner: 99 user #99
Group: 99

I tried doing a dmseg and here is what I got for the last few lines:

```

[ 1251.152296] usb 2-5.4: new high-speed USB device number 11 using ehci_hcd
[ 1251.245163] usb 2-5.4: New USB device found, idVendor=0411, idProduct=01f2
[ 1251.245167] usb 2-5.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1251.245170] usb 2-5.4: Product: USB Flash Disk
[ 1251.245173] usb 2-5.4: Manufacturer: BUFFALO
[ 1251.245175] usb 2-5.4: SerialNumber: 0916100000F102050700001567
[ 1251.246678] scsi12 : usb-storage 2-5.4:1.0
[ 1252.244681] scsi 12:0:0:0: Direct-Access     BUFFALO  USB Flash Disk   1.00 PQ: 0 ANSI: 6
[ 1252.245355] sd 12:0:0:0: Attached scsi generic sg5 type 0
[ 1252.247742] sd 12:0:0:0: [sdg] 61526016 512-byte logical blocks: (31.5 GB/29.3 GiB)
[ 1252.248297] sd 12:0:0:0: [sdg] Write Protect is on
[ 1252.248301] sd 12:0:0:0: [sdg] Mode Sense: 23 00 80 00
[ 1252.248871] sd 12:0:0:0: [sdg] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
[ 1252.259074]  sdg: sdg1 sdg2
[ 1252.261292] sd 12:0:0:0: [sdg] Attached SCSI removable disk
[ 1252.559661] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.

```


...and here is the output after I did sudo fdisk -l[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sdg'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdg: 31.5 GB, 31501320192 bytes
255 heads, 63 sectors/track, 3829 cylinders, total 61526016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1    61526015    30763007+  ee  GPT

```

I really don't know what to do from here, can someone please help me out?

Thanks! :)

---

### Post by claracc on 2013-03-09
Take a look to this link: [https://help.ubuntu.com/community/Mount/USB#USB-Device_is.2C_or_become_suddenly_read_only_without_errors](https://help.ubuntu.com/community/Mount/USB#USB-Device_is.2C_or_become_suddenly_read_only_without_errors), perhaps it can help you.

---

