---
title: "What am I missing to mount eSATA hard drive with permissions in a minimal install?"
date: 2013-07-08
forum: General Help
---

### Post by Bucky Ball on 2013-07-08
Hi all,

This problem is essentially the same but the question has changed enough to warrant a new thread. Original thread and what I've already done here:

[http://ubuntuforums.org/showthread.php?t=2159824](http://ubuntuforums.org/showthread.php?t=2159824)

Currently:
2Tb external eSATA WD GP in HDD dock plugged into Toshiba laptop.
A few installs but the two in question are Xubuntu 12.04 LTS and a Ubuntu 12.04 LTS minimal install with Xfce4 as the desktop environment. Both use PCmanFM for file manager.

My predicament:
I plug the external drive in when running Xubuntu 12.04 LTS and the two partitions on the drive are mounted with permissions.
I plug the external drive in when running Xfce4 minimal install and the two partitions appear in the left pane of PCmanFM but don't mount anywhere. 

When I right one of the partition icons in the  file manager's left pane and click>Mount Drive, I get a permissions error. Mount through terminal (to a mount point in /mnt via 'sudo mount /dev/sdb1 /mnt/sdb1') and all is fine, permissions and mounted. I even wrote scripts to mount/unmount both partitions with permissions which works fine but is a cumbersome workaround and in the best of worlds shouldn't be required.

My question:
Does anyone have any idea what might be missing from the minimal install and preventing me from mounting external devices with permissions that is installed by default in the regular 12.04 LTS Xubuntu? I've checked groups (specifically plugdev but maybe I'm missing from something else, not a guru with this), tried changing permissions. Check the saga on the link above for full details.

I am fairly convinced that as the problem is on the minimal install and the install is just that, minimal, there is something that has not been installed by default with the base kernel or any of the apps I've installed that allows me permissions for external devices. Probably a minute dependency or package that is essential.

All ideas welcome.

---

### Post by dino99 on 2013-07-08
you might glance at "users & groups" settings, to add your user

---

### Post by Bucky Ball on 2013-07-08
> **dino99 said:**
> you might glance at "users & groups" settings, to add your user

To what? As mentioned, I have checked that I am in plugdev. Any other suggestions? :-k

---

### Post by dino99 on 2013-07-08
disk, fuse, mount, admin : these should do the trick (together or not)

---

### Post by steeldriver on 2013-07-08
On my mythbuntu box it is done via udisks + libgdu0 I think (the gnome-disk-utility library - but used in non-gnome systems) - also it may be a polkit component (rather than a traditional Unix group) that actually determines whether a non-privileged user is allowed to mount / unmount

---

### Post by Bucky Ball on 2013-07-08
Thanks for the tips. When I tried adding myself to disk and fuse I was added, not already a member, but when I tried mount and admin those groups didn't exist. No message I was already a member, they're just not there. (Doing this in a terminal incidentally.) Guess I could research how to create them if they need to be there, but if they do I'd think they'd be there by default. Seems like a strange omission.

I have gvfs, polkit installed. I compared the polkit-1 sections in the udisks file regarding mounting disks and they were identical with the ones in the operational full Xubuntu install.

:-k Stumped.

Incidentally, adding myself to those groups didn't work. I used:
```

sudo adduser <username> disk
```

Naturally, with my username. Should I have added a '-g'?

---

### Post by Bucky Ball on 2013-07-09
Just an update ...

Popped an SD card in the card reader and there it was in PCmanFM, mounted and with permissions.

My conclusions (assumptions?) to this point are that my non-mounting issue is NTFS or eSATA specific and there's something missing from the Ubuntu minimal install that's causing it ... not much more than that at this point, though.

Obviously the machine is recognising the external drive partitions fine, the problem is coming when trying to mount. Is there possibly a log I can check to find the hiccough? Might plug in and check dmesg immediately after to begin with.

* Below is the dmesg after plugging the drive in. For comparison, I have included the results of the SD card first, then you can see when the external hard drive kicks in.

```
[ 8729.536534] sd 8:0:0:0: Attached scsi generic sg2 type 0
[ 8730.290295] sd 8:0:0:0: [sdb] 15523840 512-byte logical blocks: (7.94 GB/7.40 GiB)
[ 8730.291182] sd 8:0:0:0: [sdb] Write Protect is off
[ 8730.291186] sd 8:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 8730.292017] sd 8:0:0:0: [sdb] No Caching mode page present
[ 8730.292026] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 8730.296304] sd 8:0:0:0: [sdb] No Caching mode page present
[ 8730.296311] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 8730.298679]  sdb: sdb1
[ 8730.302907] sd 8:0:0:0: [sdb] No Caching mode page present
[ 8730.302914] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 8730.302920] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 8879.207575] sdb: detected capacity change from 7948206080 to 0
[ 8898.890341] usb 1-1.1: USB disconnect, device number 7
[13820.400266] ata5: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
[13820.400272] ata5: irq_stat 0x00000040, connection status changed
[13820.400277] ata5: SError: { CommWake DevExch }
[13820.400286] ata5: hard resetting link
[13826.160978] ata5: link is slow to respond, please be patient (ready=0)
[13830.027329] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[13830.073363] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[13830.210288] ata5.00: ACPI cmd ef/10:02:00:00:00:a0 (SET FEATURES) succeeded
[13830.210294] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[13830.210525] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[13830.211361] ata5.00: ATA-9: WDC WD20EZRX-00DC0B0, 80.00A80, max UDMA/133
[13830.211367] ata5.00: 3907029168 sectors, multi 0: LBA48 
[13830.213212] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[13830.213222] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[13830.213455] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) rejected by device (Stat=0x51 Err=0x04)
[13830.213626] ata5.00: configured for UDMA/133
[13830.227247] ata5: EH complete
[13830.227405] scsi 4:0:0:0: Direct-Access     ATA      WDC WD20EZRX-00D 80.0 PQ: 0 ANSI: 5
[13830.227640] sd 4:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[13830.227646] sd 4:0:0:0: [sdb] 4096-byte physical blocks
[13830.227668] sd 4:0:0:0: Attached scsi generic sg2 type 0
[13830.227770] sd 4:0:0:0: [sdb] Write Protect is off
[13830.227776] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[13830.227832] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[13830.245219]  sdb: sdb1 sdb2
[13830.246174] sd 4:0:0:0: [sdb] Attached SCSI disk
```

I ponder these:

```
[13830.213212] ata5.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) **rejected by device **(Stat=0x51 Err=0x04)
[13830.213222] ata5.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES)** filtered out**
[13830.213455] ata5.00: ACPI cmd ef/10:05:00:00:00:a0 (SET FEATURES) **rejected by device **(Stat=0x51 Err=0x04)
```


... and this:

```
[13830.227832] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, **doesn't support DPO or FUA**
```

Having little clue, I'll continue to ponder ...

---

### Post by Bucky Ball on 2013-07-09
This is very old but gives some clue:

> eSATA disks are are not auto mounted when plugged in. This is because udisks uses a heuristic to decide if it should auto mount a drive. The heuristic is motivated by the desire to not auto mount internal disks/partitions that belong to other operating systems. The heuristic currently makes the assumption that disks connected via a usb bus are external, and _disks connected with other buses ( sata, scsi ) are internal, and thus does not mount them._ This heuristic is inherently unreliable as usb disks can potentially be internal, and sas/sata disks can be external. Thus, _the heuristic needs to be disabled, and all unknown disks need to be auto mounted._ Disks detected but left unconfigured at install time should have entries in /etc/fstab set to noauto to prevent their being auto mounted.

From here:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/153768)

If this is the same issue it is quite unbelievable it is still around six years later. Does that mean we've gone from eSATAII to eSATAIII and the problem remains?

---

### Post by Bucky Ball on 2013-07-11
Thanks all. System sees eSATA as an internal drive. Needed to write a udev rule to tell it otherwise and now working great. Instructions here:

[https://wiki.archlinux.org/index.php/Udev#Detect_new_eSATA_drives](https://wiki.archlinux.org/index.php/Udev#Detect_new_eSATA_drives)

(Thanks to Bashing-om for keeping the clues coming on the other thread.)

Take note: plug in, appears in file manager, but doesn't automount (mine didn't). Just click it. Good luck.

* I have posted a step-by-step here:

[http://ubuntuforums.org/showthread.php?t=2161837&p=12728219#post12728219](http://ubuntuforums.org/showthread.php?t=2161837&p=12728219#post12728219)

;)

---

