---
title: "Ubuntu 12.10/11.10 64-bit usb boot problem"
date: 2012-10-19
forum: General Help
---

### Post by dobri on 2012-10-19
Hi guys,

I've been trying to run ubuntu directly from usb (without installing it) but with no success. While booting, the computer halts and some error messages like "device descriptor read/8, error -110" are shown on the screen.

Here is the log from ubuntu 11.10:

```

[6.875902] [drm] nouveau 0000:02:00.0: allocated 1280x1024 fb: 0x40000000, bo ffff88007a3b4800
[6.876058] fbcon: nouveaufb(fb0) is primary device 
[6.923528] Console: switching to colour frame buffer device 160x64
[6.924751] fb0: nouveaufb frame buffer device
[6.924758] drm: registered panic notifier 
[6.924772] [drm] Initialized nouveau 0.0.16 20090420 for 0000:02:00.0 on minor 0

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

[86.128114] usb 1-3: device descriptor read/8, error -110
[86.232031] hub 1-0:1.0: unable to enumerate USB device on port 3
[86.368016] usb 1-4: new high speed USE device number 6 using ehci_hcd
[86.506475] usbcore: registered new interface driver uas
[86.507534] Initializing USE Mass Storage driver...
[86.507879] scsi4 : usb-storage 1-4:1.0
[86.508031] usbcore: registered new interface driver usb-storage
[86.508042] USB Mass Storage support registered.
[86.804016] usb 2-3: new full speed US B device number 2 using ohci_hcd
[87.505037] scsi 4:0:0:0: Direct-Access A-DATA USP Flash Drive 0.00 PQ: 0 ANSI: 2
[87.508873] sd 4:0:0:0: Attached scsi generic sg3 type 0
[87.510172] sd 4:0:0:0: [sdc] 3948544 512-byte logical blocks: (2.02 08/1.88 GiB)
[87.510896] sd 4:0:0:0: [sdc] Write Protect is elf
[87.511635] sd 4:0:0:0: [sdc] Asking for cache data failed
[87.511644] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[87.515008] sd 4:0:0:0: [sdc] Asking for cache data failed
[87.515022] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[87.615641] sdc: sdcl
[87.618392] sd 4:0:0:0: [sdc] Asking for cache data failed
[87.618412] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[87.6184231 sd 4:0:0:0: [sdc] Attached SCSI removable disk
[101.980019] usb 2-3: device descriptor read/64, error -110
[117.260020] usb 2-3: device descriptor read/64, error -110
[117.540014] usb 2-3: new full speed USB device number 3 using ohci_hcd
[132.716013] usb 2-3: device descriptor read/64, error -110
[147.996013] usb 2-2; device descriptor read/64, error -110
[148.276013] usb 2-3: new full speed USB device number 4 using ohci_hcd
[153.297019] usb 2-3: device descriptor read/8, error -110
[158.417025] usb 2-3: device descriptor read/8, error -110
[158.696013) usb 2-3: new full speed USB device number 5 using ohci_hcd
[163.717021] usb 2-3: device descriptor read/8, error -110
[160.837012] usb 2-3: device descriptor read/8, error -110
[168.940025] hub 2-0:1.0: unable to enumerate USE device on port 3

```

I made a bootable usb with Universal usb installer. Tested with both ubuntu 12.10 and 11.10 64-bit, exactly the same situation.

Any ideas how to fix this problem?

---

### Post by efflandt on 2012-10-19
I have never used the Universal USB Installer.  But if you either have a working Ubuntu system or live/install CD for either of those versions, I have never had problems with **Startup Disk Creator** in Ubuntu unless I accidentally format the entire device instead of a partition on it.  If that happens I fix it with gparted, recreating an msdos partition table and FAT32 partition.

---

### Post by dobri on 2012-10-19
No, I do not have neither working ubuntu system, nor installation CD (besides ubuntu 12.10 iso file is too large for ordinary CD :()

Here is the *casper.log* (in case it can be useful in solving the problem)

```

Begin: 
Running /scripts/casper-premount ... 
done.
done.
stdin: error 0

/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found
stdin: error 0
/init: line 7: can't open /dev/sr0: No medium found
/init: line 7: can't open /dev/sr0: No medium found
Unable to find a medium containing a live file system

```

---

