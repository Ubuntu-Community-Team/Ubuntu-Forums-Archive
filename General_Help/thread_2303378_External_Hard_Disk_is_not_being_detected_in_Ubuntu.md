---
title: "External Hard Disk is not being detected in Ubuntu 12.04"
date: 2015-11-18
forum: General Help
---

### Post by Girish_Aligati on 2015-11-18
Hi, 

My external hard disk (WD 750 GB My Passport 730)was accidentally unplugged,after this I could not access the hard disk. 

Below are the instructions(from "dmesg" command) after immediately connecting my hard disk 
{
[ 3314.691857] usb 1-6: New USB device found, idVendor=1058, idProduct=0730
[ 3314.691870] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3314.691877] usb 1-6: Product: My Passport 0730
[ 3314.691884] usb 1-6: Manufacturer: Western Digital
[ 3314.691890] usb 1-6: SerialNumber: 575846314143303336393733
[ 3314.693057] usb-storage 1-6:1.0: USB Mass Storage device detected
[ 3314.693199] scsi6 : usb-storage 1-6:1.0
[ 3316.764930] scsi 6:0:0:0: Direct-Access     WD       My Passport 0730 1015 PQ: 0 ANSI: 6
[ 3316.765782] scsi 6:0:0:1: Enclosure         WD       SES Device       1015 PQ: 0 ANSI: 6
[ 3316.766105] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 3316.766185] ses 6:0:0:1: Attached Enclosure device
[ 3316.766237] ses 6:0:0:1: Attached scsi generic sg3 type 13
[ 3336.685291] sd 6:0:0:0: [sdc] Spinning up disk...
[ 3366.988103] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3370.616299] [sched_delayed] \x014CE: hpet increased min_delta_ns to 20115 nsec
[ 3411.980032] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3456.972035] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3502.028130] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3546.956134] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3592.012115] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3607.712308] ......not responding...
[ 3717.712816] sd 6:0:0:0: [sdc] 1465081856 512-byte logical blocks: (750 GB/698 GiB)
[ 3717.713526] sd 6:0:0:0: [sdc] Write Protect is off
[ 3717.713537] sd 6:0:0:0: [sdc] Mode Sense: 47 00 10 08
[ 3717.714213] sd 6:0:0:0: [sdc] No Caching mode page found
[ 3717.714222] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 3738.711374] sd 6:0:0:0: [sdc] Spinning up disk...
[ 3768.940124] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3813.964330] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3859.020132] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3903.948053] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3949.004326] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 3993.932113] usb 1-6: reset high-speed USB device number 3 using ehci-pci
[ 4009.628307] ......not responding...
[ 4119.629800] sd 6:0:0:0: [sdc] No Caching mode page found
[ 4119.629811] sd 6:0:0:0: [sdc] Assuming drive cache: write through
}

---

### Post by Bucky Ball on 2015-11-18
With the hard drive plugged in and switched on, give us the output of:

```
lsusb
```

... if it is USB external disk, and:

```
sudo blkid
```

Please use code tags for code. (See last link in my signature.)

---

### Post by Girish_Aligati on 2015-11-30
Hi,
Below is the output for "sudo blkid"
```

 /dev/sda1: LABEL="System Reserved" UUID="54D83A12D839F2BA" TYPE="ntfs" 
/dev/sda2: UUID="F0CA4E4CCA4E0F72" TYPE="ntfs" 
/dev/sda3: UUID="1441-76BA" TYPE="vfat" 
/dev/sda5: UUID="d9645e7d-3a29-4240-b0ca-39b90783ec23" TYPE="ext4" 
/dev/sda6: UUID="ab0761dc-71fb-439e-a297-cafc3c8ef0a2" TYPE="swap" 

```

and the output for "lsusb"
```
 
Bus 002 Device 002: ID 090c:7371 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1058:0730 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

---

