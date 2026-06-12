---
title: "One mounts, the other doesn't :-("
date: 2020-08-23
forum: General Help
---

### Post by canadabob on 2020-08-23
I'm sort of new to Ubuntu so some of it is still a mystery to me...

Today's mystery is why a USB won't mount, I have two identical USB sticks, one mounts as soon as it's plugged in, the other isn't recognised.
I can find my way to it with gparted to format it, but I can't get the stick to mount, yet the other identical stick does.

I'd appreciate any pointers, not sure if the info below helps ? 
```

[255668.093489] usb 1-4: Product: USB Flash Drive
[255668.093492] usb 1-4: Manufacturer: Philips
[255668.093494] usb 1-4: SerialNumber: 0708648D1F1C7440
[255668.095178] usb-storage 1-4:1.0: USB Mass Storage device detected
[255668.095543] scsi host0: usb-storage 1-4:1.0
[255669.116473] scsi 0:0:0:0: Direct-Access     Philips  USB Flash Drive  PMAP PQ: 0 ANSI: 6
[255669.116920] sd 0:0:0:0: Attached scsi generic sg0 type 0
[255669.117366] sd 0:0:0:0: [sda] 30302208 512-byte logical blocks: (15.5 GB/14.4 GiB)
[255669.117596] sd 0:0:0:0: [sda] Write Protect is off
[255669.117599] sd 0:0:0:0: [sda] Mode Sense: 45 00 00 00
[255669.117852] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[255669.341478]  sda:
[255669.343461] sd 0:0:0:0: [sda] Attached SCSI removable disk
[255683.586593]  sda:
[255683.784285]  sda:
[258726.286135] usb 1-4: USB disconnect, device number 41
[258890.759943] wlp0s20f3: authenticate with 20:b0:01:c5:39:55
[258890.762287] wlp0s20f3: send auth to 20:b0:01:c5:39:55 (try 1/3)
[258890.787586] wlp0s20f3: authenticated
[258890.790734] wlp0s20f3: associate with 20:b0:01:c5:39:55 (try 1/3)
[258890.795208] wlp0s20f3: RX AssocResp from 20:b0:01:c5:39:55 (capab=0x1011 status=0 aid=6)
[258890.798847] wlp0s20f3: associated
[258890.846434] wlp0s20f3: Limiting TX power to 20 (20 - 0) dBm as advertised by 20:b0:01:c5:39:55
[258924.342901] wlp0s20f3: deauthenticated from 20:b0:01:c5:39:55 (Reason: 2=PREV_AUTH_NOT_VALID)
[258925.002597] wlp0s20f3: authenticate with 22:b0:01:c5:39:5d
[258925.006221] wlp0s20f3: send auth to 22:b0:01:c5:39:5d (try 1/3)
[258925.029405] wlp0s20f3: authenticated
[258925.029587] wlp0s20f3: associate with 22:b0:01:c5:39:5d (try 1/3)
[258925.031450] wlp0s20f3: RX AssocResp from 22:b0:01:c5:39:5d (capab=0x1011 status=0 aid=1)
[258925.033625] wlp0s20f3: associated
[258925.112644] wlp0s20f3: Limiting TX power to 23 (23 - 0) dBm as advertised by 22:b0:01:c5:39:5d
[259930.439233] usb 1-4: new high-speed USB device number 42 using xhci_hcd
[259930.712925] usb 1-4: New USB device found, idVendor=13fe, idProduct=5400, bcdDevice= 1.10
[259930.712930] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[259930.712933] usb 1-4: Product: USB Flash Drive
[259930.712936] usb 1-4: Manufacturer: Philips
[259930.712938] usb 1-4: SerialNumber: 0708648D1F1C7440
[259930.714721] usb-storage 1-4:1.0: USB Mass Storage device detected
[259930.715356] scsi host0: usb-storage 1-4:1.0
[259931.740845] scsi 0:0:0:0: Direct-Access     Philips  USB Flash Drive  PMAP PQ: 0 ANSI: 6
[259931.741427] sd 0:0:0:0: Attached scsi generic sg0 type 0
[259931.742510] sd 0:0:0:0: [sda] 30302208 512-byte logical blocks: (15.5 GB/14.4 GiB)
[259931.742779] sd 0:0:0:0: [sda] Write Protect is off
[259931.742782] sd 0:0:0:0: [sda] Mode Sense: 45 00 00 00
[259931.743040] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[259931.975830]  sda:
[259931.977896] sd 0:0:0:0: [sda] Attached SCSI removable disk
[263163.619800] debugfs: File 'le_min_key_size' in directory 'hci0' already present!
[263163.619803] debugfs: File 'le_max_key_size' in directory 'hci0' already present!
[264345.945496] wlp0s20f3: authenticate with 20:b0:01:c5:39:55
[264345.948447] wlp0s20f3: send auth to 20:b0:01:c5:39:55 (try 1/3)
[264345.973684] wlp0s20f3: authenticated
[264345.977144] wlp0s20f3: associate with 20:b0:01:c5:39:55 (try 1/3)
[264345.981156] wlp0s20f3: RX AssocResp from 20:b0:01:c5:39:55 (capab=0x1011 status=0 aid=6)
[264345.983554] wlp0s20f3: associated
[264346.075021] wlp0s20f3: Limiting TX power to 20 (20 - 0) dBm as advertised by 20:b0:01:c5:39:55
[264399.048050] wlp0s20f3: deauthenticated from 20:b0:01:c5:39:55 (Reason: 2=PREV_AUTH_NOT_VALID)
[264399.825591] wlp0s20f3: authenticate with 22:b0:01:c5:39:5d
[264399.829457] wlp0s20f3: send auth to 22:b0:01:c5:39:5d (try 1/3)
[264399.853133] wlp0s20f3: authenticated
[264399.855456] wlp0s20f3: associate with 22:b0:01:c5:39:5d (try 1/3)
[264399.857190] wlp0s20f3: RX AssocResp from 22:b0:01:c5:39:5d (capab=0x1011 status=0 aid=1)
[264399.859316] wlp0s20f3: associated
[264399.921321] wlp0s20f3: Limiting TX power to 23 (23 - 0) dBm as advertised by 22:b0:01:c5:39:5d
[265724.844270] usb 1-4: USB disconnect, device number 42
[265731.535908] usb 1-4: new high-speed USB device number 43 using xhci_hcd
[265731.800911] usb 1-4: New USB device found, idVendor=13fe, idProduct=5400, bcdDevice= 1.10
[265731.800916] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[265731.800919] usb 1-4: Product: USB Flash Drive
[265731.800921] usb 1-4: Manufacturer: Philips
[265731.800923] usb 1-4: SerialNumber: 0708648D1F1C7440
[265731.802641] usb-storage 1-4:1.0: USB Mass Storage device detected
[265731.802970] scsi host0: usb-storage 1-4:1.0
[265732.813637] scsi 0:0:0:0: Direct-Access     Philips  USB Flash Drive  PMAP PQ: 0 ANSI: 6
[265732.814213] sd 0:0:0:0: Attached scsi generic sg0 type 0
[265732.815154] sd 0:0:0:0: [sda] 30302208 512-byte logical blocks: (15.5 GB/14.4 GiB)
[265732.815386] sd 0:0:0:0: [sda] Write Protect is off
[265732.815390] sd 0:0:0:0: [sda] Mode Sense: 45 00 00 00
[265732.815616] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[265733.040330]  sda:
[265733.042237] sd 0:0:0:0: [sda] Attached SCSI removable disk
[266438.743760] usb 1-4: USB disconnect, device number 43
[266451.662384] usb 1-4: new high-speed USB device number 44 using xhci_hcd
[266451.875430] usb 1-4: New USB device found, idVendor=13fe, idProduct=5400, bcdDevice= 1.10
[266451.875435] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[266451.875438] usb 1-4: Product: USB Flash Drive
[266451.875440] usb 1-4: Manufacturer: Philips
[266451.875442] usb 1-4: SerialNumber: 0708648B241B9F07
[266451.877227] usb-storage 1-4:1.0: USB Mass Storage device detected
[266451.877661] scsi host0: usb-storage 1-4:1.0
[266452.887929] scsi 0:0:0:0: Direct-Access     Philips  USB Flash Drive  PMAP PQ: 0 ANSI: 6
[266452.888605] sd 0:0:0:0: Attached scsi generic sg0 type 0
[266452.889529] sd 0:0:0:0: [sda] 30302208 512-byte logical blocks: (15.5 GB/14.4 GiB)
[266452.889825] sd 0:0:0:0: [sda] Write Protect is off
[266452.889828] sd 0:0:0:0: [sda] Mode Sense: 45 00 00 00
[266452.890094] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[266453.038584]  sda: sda1
[266453.041349] sd 0:0:0:0: [sda] Attached SCSI removable disk
[266453.266472] FAT-fs (sda1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[266765.543022] usb 1-4: USB disconnect, device number 44
[266774.376489] usb 1-4: new high-speed USB device number 45 using xhci_hcd
[266774.654350] usb 1-4: New USB device found, idVendor=13fe, idProduct=5400, bcdDevice= 1.10
[266774.654355] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[266774.654358] usb 1-4: Product: USB Flash Drive
[266774.654360] usb 1-4: Manufacturer: Philips
[266774.654362] usb 1-4: SerialNumber: 0708648D1F1C7440
[266774.656180] usb-storage 1-4:1.0: USB Mass Storage device detected
[266774.656509] scsi host0: usb-storage 1-4:1.0
[266775.662115] scsi 0:0:0:0: Direct-Access     Philips  USB Flash Drive  PMAP PQ: 0 ANSI: 6
[266775.662729] sd 0:0:0:0: Attached scsi generic sg0 type 0
[266775.663659] sd 0:0:0:0: [sda] 30302208 512-byte logical blocks: (15.5 GB/14.4 GiB)
[266775.663908] sd 0:0:0:0: [sda] Write Protect is off
[266775.663911] sd 0:0:0:0: [sda] Mode Sense: 45 00 00 00
[266775.664136] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[266775.892029]  sda:
[266775.894530] sd 0:0:0:0: [sda] Attached SCSI removable disk
[266927.234368] usb 1-4: USB disconnect, device number 45
[266966.391195] usb 1-4: new high-speed USB device number 46 using xhci_hcd
[266966.672120] usb 1-4: New USB device found, idVendor=13fe, idProduct=5400, bcdDevice= 1.10
[266966.672124] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[266966.672127] usb 1-4: Product: USB Flash Drive
[266966.672130] usb 1-4: Manufacturer: Philips
[266966.672132] usb 1-4: SerialNumber: 0708648D1F1C7440
[266966.673858] usb-storage 1-4:1.0: USB Mass Storage device detected
[266966.674240] scsi host0: usb-storage 1-4:1.0
[266967.688572] scsi 0:0:0:0: Direct-Access     Philips  USB Flash Drive  PMAP PQ: 0 ANSI: 6
[266967.689144] sd 0:0:0:0: Attached scsi generic sg0 type 0
[266967.689907] sd 0:0:0:0: [sda] 30302208 512-byte logical blocks: (15.5 GB/14.4 GiB)
[266967.690141] sd 0:0:0:0: [sda] Write Protect is off
[266967.690145] sd 0:0:0:0: [sda] Mode Sense: 45 00 00 00
[266967.690387] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[266967.927993]  sda:
[266967.929617] sd 0:0:0:0: [sda] Attached SCSI removable disk
bob@ThinkPad-L13:~$
```

---

### Post by Autodave on 2020-08-23
First thing is to try another port.  I have one here that only likes one port outta 8 on this machine.  Any other machine and it likes any port.  Why?  Dunno.  It's just the way it is sometimes.

Try another machine, too.  You may have a failed stick.

---

### Post by zebra2 on 2020-08-23
I have the same experience with USB's as in post #2.  However plug in the problem USB.  Open "Disks" and see if your USB is listed. It may be there but not mounted.  If it is there but not mounted you can click on the USB and then mount it by clicking the right arrow Icon below the USB box. It is kind of common for a USB not to mount but your system will still know that it is there. You just have to mount it manually.

---

### Post by TheFu on 2020-08-23
> **zebra2 said:**
> I have the same experience with USB's as in post #2.  However plug in the problem USB.  Open "Disks" and see if your USB is listed. It may be there but not mounted.  If it is there but not mounted you can click on the USB and then mount it by clicking the right arrow Icon below the USB box. It is kind of common for a USB not to mount but your system will still know that it is there. You just have to mount it manually.

There are methods where USB storage gets automatically mounted when used. Most people new to Linux don't bother with this setup, because it isn't point-n-click, but it can be significantly faster than the point-n-click mount method.  For moving 20G of files, it probably doesn't matter, but when moving more than that, I'd want the best performance possible.  That means manually editing system files.

---

### Post by Impavidus on 2020-08-24
Maybe the filesystem is damaged. What filesystem is on the usb stick? Usually it's fat32 on smaller ones, exfat or ntfs on larger ones, i.e., Windows filesystems. It may need a check (in case of a Windows filesystem, use Windows). I usually just format if a filesystem on a usb stick (or an sd card) is damaged. Sometimes you can still mount it read-only from command line.

---

### Post by canadabob on 2020-08-24
> **Autodave said:**
> First thing is to try another port.  I have one here that only likes one port outta 8 on this machine.  Any other machine and it likes any port.  Why?  Dunno.  It's just the way it is sometimes.

Try another machine, too.  You may have a failed stick.

Thanks for the suggestions above, I tried other ports and other machines too, but the problem remains :-(

---

### Post by canadabob on 2020-08-24
Well Zebra2 you put me on the right direction, I did as suggested above, but I didn't have the **right arrow icon below the USB box, **I didn't have a "mount" option either, but I noticed that the USB didn't have a partition, it was all FREE SPACE, so, more in hope than expertise I made a 0.5g partition leaving 15.5g FREE SPACE, are you ahead of me yet :-) that did the trick, the USB is now recognised and I can read & write on it. I have no idea why the above did the trick, or how one of the two identical sticks didn't have a partition on it, or even why not having a small partition would cause the problem, the partition is empty, nothing in it, but the stick is working now ?

Thanks Zebra2 and everyone else for taking the time to respond, it's been valued and appreciated, maybe one of you could explain why the partition did the trick...

Bob.

---

### Post by canadabob on 2020-08-24
To add to the mystery, I just plugged in the stick that doesn't have a problem, but this one doesn't seem to have a partition, here's what DISKS reports...

Model:             Philips USB Flash Drive (PMAP)
Size:               16 GB (15,514,730,496 bytes)
Partitioning:    Master Boot Record

**VOLUMES:**

Size:                16 GB &#8212; 15 GB free (0.1% full)
Device:             /dev/sda1
UUID:               C2E1-659E
Partition Type:  W95 FAT32 (LBA) (Bootable)
Contents:          FAT (32-bit version) &#8212; Mounted at /media/bob/LINUX MINT

The USB that I had trouble with now reads as follows...

Model:             Philips USB Flash Drive (PMAP)
Size:                16 GB (15,514,730,496 bytes)
Partitioning:     GUID Partition Table

Size:                 515 MB &#8212; 514 MB free (0.2% full) the rest is FREE SPACE.
Device:             /dev/sda1
Partitioning:      3FF4-3EDA
Partition Type:  Basic Data
Contents:          FAT (16-bit version) &#8212; Mounted at /media/bob/USB

The 0.2% above is a small file that I copied to the problem USB to see if I could write to it, now that it's mounted, I see it wrote that file to the first Partition, if the file had been say 3g would that have automatically gone to the 15.5 Free Space ?

---

### Post by canadabob on 2020-08-24
Both sticks were/are FAT 32, I tried reformatting the problem stick, even the hard format, made no difference, the stick still wouldn't mount, but by adding a partition it's working now, can't imagine why, the other/good stick doesn't seem to be partitioned.

---

### Post by TheFu on 2020-08-24
All storage devices should have a partition table. Software expects that AND it is the "best practice".  People do ignore this, especially people setting up RAID systems at their own peril.

If you'd like better performance that supports Unix permissions, great a GPT partition table, create a partition, then format it with f2fs. This is a file system designed for flash storage devices. It routinely tests to be very fast, often faster than ext4, which is pretty impressive. It has kernel-level drivers, so it won't be slow like FUSE file systems and when you mount it, chmod and chown all work.  The downside to f2fs is that Windows and most camera support doesn't exist to my knowledge. Perhaps WSL can access it?

If you are stuck with FAT32, then the mount options are the only way to control the owner, group and permissions. Only 1 set of permissions is possible for all files on the storage that way, unfortunately. There are lots of mount examples and fstab examples in these forums. Look for 'vfat' and 'mount' when you search.

---

### Post by Impavidus on 2020-08-24
Both drives now have a partition table. The first has one in MBR style, the second in GPT style. GPT is modern and has some advantages, but for a 16GB stick it doesn't really matter. That you now have a GPT partition table tells us that you formatted the drive, so any damaged partitions or filesystems have been deleted and a new, clean partition has been created. It's only 500MB, the remaining 15.5GB is currently unusable because unallocated. You can use your favourite partitioning tool to make the whole drive usable again.

I assume my guess of a damaged filesystem was more or less correct. Pulling the usb stick out of the computer before unmounting the filesystem may cause filesystem damage. It may also be a broken drive. They don't last forever.

---

### Post by canadabob on 2020-08-25
Thanks for the pointers, the problem is sorted now, and I have a better understanding of what was wrong.

---

