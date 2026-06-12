---
title: "Usb stick won't work"
date: 2007-04-09
forum: General Help
---

### Post by lhabjane on 2007-04-09
I've bought 10 usb sticks, but they won't work under Ubuntu. (heh, didn't know that I must carefully choose such trivial hardware for linux) 

They are somehow special, because they have two partitions (in windows disk management they are seen as two hardware separated disks). One for data, one for special encryption software.

After I plugin the stick nothing happens! (Tried at least 5 other brand sticks, they all automatically mount). After some time, I can't even get lsusb (nothing happens)
but, this is my shortly-after-pluging-in lsusb

```
 Bus 004 Device 006: ID 1005:b113 Apacer Technology, Inc. Handy Steno 2.0 (256MB)
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  

```

Do I must say that my stick ISN'T Apacer 256, it's Canyon 1GB :) 

dmesg output
```

[17181208.780000] usb 4-7: new high speed USB device using ehci_hcd and address 5
[17181214.872000] usb 4-7: new high speed USB device using ehci_hcd and address 6
[17181215.008000] usb 4-7: configuration #1 chosen from 1 choice
[17181215.008000] scsi1 : SCSI emulation for USB Mass Storage devices
[17181215.008000] usb-storage: device found at 6
[17181215.008000] usb-storage: waiting for device to settle before scanning
[17181217.908000] usb 4-7: USB disconnect, address 6
[17181433.608000] usb 4-7: new high speed USB device using ehci_hcd and address 7
[17181433.744000] usb 4-7: configuration #1 chosen from 1 choice
[17181433.744000] scsi2 : SCSI emulation for USB Mass Storage devices
[17181433.744000] usb-storage: device found at 7
[17181433.744000] usb-storage: waiting for device to settle before scanning
[17181438.744000] usb-storage: device scan complete
[17181438.744000]   Vendor:           Model: USB FLASH DRIVE   Rev: 34CH
[17181438.744000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17181438.744000]   Vendor:           Model: USB FLASH DRIVE   Rev: 34CH
[17181438.744000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17181438.944000] SCSI device sda: 2012160 512-byte hdwr sectors (1030 MB)
[17181438.944000] sda: Write Protect is off
[17181438.944000] sda: Mode Sense: 23 00 00 00
[17181438.944000] sda: assuming drive cache: write through
[17181438.948000] SCSI device sda: 2012160 512-byte hdwr sectors (1030 MB)
[17181438.948000] sda: Write Protect is off
[17181438.948000] sda: Mode Sense: 23 00 00 00
[17181438.948000] sda: assuming drive cache: write through
[17181438.948000]  sda:<6>usb 4-7: reset high speed USB device using ehci_hcd and address 7
[17181472.172000] usb 4-7: device descriptor read/64, error -110

```

Please help, I don't want to buy another 10 sticks!

---

### Post by bettlebrox on 2007-04-09
The software used on these to enable the encryption only works with windows. If you want the stick to work try reformating  the stick and removing the encryption and that *might* do the trick.

---

### Post by lhabjane on 2007-04-10
I can't format stick in windows and delete partitions because it appears as two separate disks. And, the software is just here to encrypt if you want, I don't use it, and reading stick works on windows without ANY drivers/configuration. (I know, cos I can read/write on Vista, and that software doesn't work on Vista)

Can I delete partitions on Ubuntu?

---

### Post by n3gbz on 2007-04-10
Either Gparted (gnome) or QTparted (kde) are the easiest tools for repartitioning and should do the trick. 

If there is a u3 partition then it is a little more complicated, but nothing on the Canyon website indicates u3.   

Please post your results.

---

### Post by lhabjane on 2007-04-10
Installed Gparted, but I can only see my harddisk, nothing else.. and when I type fdisk -l my stick isn't listed. And after some time, when my stick is plugged in, it disappears from lsusb. Weird.

---

### Post by n3gbz on 2007-04-10
I assume you used Gparted in Ubuntu.  My next try would be to burn a Gparted LiveCD from 

[http://sourceforge.net/projects/gparted/](http://sourceforge.net/projects/gparted/) 

and hope that might work better.   

Beyond that, I have no idea at the moment.

---

### Post by lhabjane on 2007-04-10
I highly doubt this will help. But I've sent an e-mail to Canyon support, maybe they will help, as there is already some info about this on theirs FAQ

And, when it disappers from usb, i get this
```

kasa@kasa-laptop:~$ cat /proc/scsi/scsi 
Attached devices:
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor:          Model: USB FLASH DRIVE  Rev: 34CH
  Type:   Direct-Access                    ANSI SCSI revision: 02
Host: scsi1 Channel: 00 Id: 00 Lun: 01
  Vendor:          Model: USB FLASH DRIVE  Rev: 34CH
  Type:   Direct-Access                    ANSI SCSI revision: 02

```

---

### Post by lhabjane on 2007-04-15
No reply from them. Maybe somebody knows something about this specific problem? scsi emulation or something?

---

