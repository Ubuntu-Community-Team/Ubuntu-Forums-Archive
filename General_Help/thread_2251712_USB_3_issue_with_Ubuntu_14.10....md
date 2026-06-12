---
title: "USB 3 issue with Ubuntu 14.10..."
date: 2014-11-06
forum: General Help
---

### Post by andrew.t.sullivan on 2014-11-06
Is there a known issue with USB 3 ports in Ubuntu 14.10?  I ask because I have the following problem with using an external USB HD with my Lenovo G505s laptop.
[INDENT]
If I plug the drive in to the USB 3 port and boot into Windows 8.1, everything is fine.

If I restart the laptop, leaving the drive plugged in, and boot into Ubuntu 14.10, everything is fine.

If I power down the laptop (again, leaving the  drive plugged in) and boot into Ubuntu, the drive is not detected.

If I repeat the last step but have the drive plugged into a USB 2 port, everything is fine (except I guess the read/write speeds will be lower).
[/INDENT]

Any thoughts?

Thanks

Andrew

---

### Post by Bucky Ball on 2014-11-06
Have you tried right clicking and fully unmounting the partitions on the drive prior to rebooting? Just a thought to get the ball rolling ... :-k

---

### Post by andrew.t.sullivan on 2014-11-06
If by "right clicking and fully unmounting the partitions on the drive" you mean "Safely Remove", yes, tried that, made no difference - still can't see the drive when it's plugged into the USB 3 port.

---

### Post by Bucky Ball on 2014-11-06
Try [HERE]("http://ubuntuforums.org/showthread.php?t=2218891&page=2&p=13122368#post13122368") and answer 1 [HERE]("http://askubuntu.com/questions/50866/external-usb-3-0-hard-drive-is-not-recognised-when-plugged-into-usb-3-port").

Quickly dug up on a trawl through [HERE]("https://duckduckgo.com/?q=usb+3+port+not+recognised+ubuntu").

Hopefully that gives some clues.

---

### Post by andrew.t.sullivan on 2014-11-06
Thanks for that, seems there is an issue.  I don't understand why Ubuntu can "see" the drive on USB 3 after a restart from W8.1 but not after a cold start?

FWIW here is the output from lsusb:

Bus 002 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 5986:0295 Acer, Inc 
Bus 001 Device 006: ID 1058:0820 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 003: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Bucky Ball on 2014-11-06
Try this command with the USB3 drive plugged in:

```
sudo blkid
```

Also, does Gparted see it? Install Gparted if you don't have it and have a look. It should be sdb or sdc, depending on what other devices you have in and outside.

---

### Post by andrew.t.sullivan on 2014-11-06
This is the output from blkid:

```

/dev/sda1: LABEL="WINRE_DRV" UUID="B29254B692548131" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="f528bca8-fa97-460a-8684-1ce32fe86567" 
/dev/sda2: LABEL="SYSTEM_DRV" UUID="4257-09B9" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="949de4d9-61c4-4d9e-a1ca-b047fa3aaf7e" 
/dev/sda3: LABEL="LRS_ESP" UUID="6C57-6130" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="062ad81f-8460-4fe3-a060-35f7397e5526" 
/dev/sda4: PARTLABEL="Microsoft reserved partition" PARTUUID="010b392c-74db-4884-baf8-d71b987437d9" 
/dev/sda5: LABEL="Windows8_OS" UUID="B0605B08605AD4A6" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="eaa14ad6-8ddc-4c68-9278-59306425ffb9" 
/dev/sda6: UUID="299e2eeb-d328-4de8-9f68-de6522ec9aa2" TYPE="swap" PARTLABEL="primary" PARTUUID="28760370-0359-4754-a79b-d70b972b1fce" 
/dev/sda7: LABEL="Ubuntu /" UUID="c1e77096-e313-490c-9543-df0eb1ea17d5" TYPE="ext4" PARTUUID="67034f69-2506-4d80-b4a5-660c5d265ee4" 
/dev/sda9: UUID="F69ACB649ACB1FCB" TYPE="ntfs" PARTUUID="f4414039-446c-41b7-a671-293bce7343a8" 
/dev/sda10: LABEL="LENOVO" UUID="F8F262BEF26280AC" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="ab05cd1f-6ea4-4ad0-8fd5-1f88a7f064b7" 
/dev/sda11: LABEL="PBR_DRV" UUID="56425DC1425DA691" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="be937ea9-fdc0-4797-b2d7-c2d24359d862" 
/dev/sda13: LABEL="Ubuntu /Home" UUID="c22c5a26-c253-4f0c-a48e-223db57d93f2" TYPE="ext4" PARTUUID="db094f3e-c4d5-483f-ae02-84f7a925e78d" 

```

They all seem to be partitions on my internal drive?

The version of gparted that comes with Ubuntu does not see the externaldrive when it's plugges into the USB 3 port.

---

### Post by Bucky Ball on 2014-11-06
But I'm presuming that this:

```
Bus 001 Device 006: ID 1058:0820 Western Digital Technologies, Inc. 
```

From lsusb is the hard drive?

(PS: Please use [code] tags when posting code. See the last link in my signature.)

---

### Post by andrew.t.sullivan on 2014-11-06
Indeed.  The drive is a WD My Passport Ultra 1TB drive.

Point taken about  using [code tags, I&#8217;ll do that in future.

---

