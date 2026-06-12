---
title: "Custom Kernel and Feisty Issue"
date: 2007-04-21
forum: General Help
---

### Post by katzman on 2007-04-21
HI there;
So i have gotten a custom kernel compiled from vanilla sources plus a patch or two and it is all working okay except for a couple of things which i have not found an answer for
NOTE: these also occur with a kernel compile from ubuntu sources

1)I have a usb hardrive....when using the ubuntu generic kernel i can plug it in and it mounts like normal to /media/disk...but with the custom kernels it is not being automounted.....i can mount it manually but that is a pain in the reat

2)more of a minor one....but i know that the new kernels are supposed to be using a unified s/pata drive and so your ide drives will show up as sda1,sda2,sdb1...etc etc....
this is the case with the generic kernel but not with either of the custom.Anyone know the reason for this and if i should fix it?

Thanks in advance

---

### Post by skip27 on 2007-04-21
Question: are you using autofs? If not, are you using udev? I personally use udev rules to "automount" my external drives, which basically gives me the freedom to use any kernel I want as long as it has udev support compiled in.

---

### Post by katzman on 2007-04-21
as far as i know udev but i cannot recall seeing anuthing udev related in the kernel and can't find it in .config
anyway some more data can't hurt:
as you can see the disk is being registered okay...but just not mounted....

dmesg:
[  762.487000] usb 1-6: new high speed USB device using ehci_hcd and address 3
[  762.603000] usb 1-6: configuration #1 chosen from 1 choice
[  762.751000] scsi1 : SCSI emulation for USB Mass Storage devices
[  762.752000] usb-storage: device found at 3
[  762.752000] usb-storage: waiting for device to settle before scanning
[  767.754000] scsi 1:0:0:0: Direct-Access     Maxtor 6 Y080L0           0000 PQ: 0 ANSI: 0
[  767.755000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[  767.756000] sda: Write Protect is off
[  767.756000] sda: Mode Sense: 27 00 00 00
[  767.756000] sda: assuming drive cache: write through
[  767.757000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[  767.758000] sda: Write Protect is off
[  767.758000] sda: Mode Sense: 27 00 00 00
[  767.758000] sda: assuming drive cache: write through
[  767.758000]  sda: sda1
[  767.775000] sd 1:0:0:0: Attached scsi disk sda
[  767.775000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  767.778000] usb-storage: device scan complete


udev:

[  762.487000] usb 1-6: new high speed USB device using ehci_hcd and address 3
[  762.603000] usb 1-6: configuration #1 chosen from 1 choice
[  762.751000] scsi1 : SCSI emulation for USB Mass Storage devices
[  762.752000] usb-storage: device found at 3
[  762.752000] usb-storage: waiting for device to settle before scanning
[  767.754000] scsi 1:0:0:0: Direct-Access     Maxtor 6 Y080L0           0000 PQ: 0 ANSI: 0
[  767.755000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[  767.756000] sda: Write Protect is off
[  767.756000] sda: Mode Sense: 27 00 00 00
[  767.756000] sda: assuming drive cache: write through
[  767.757000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[  767.758000] sda: Write Protect is off
[  767.758000] sda: Mode Sense: 27 00 00 00
[  767.758000] sda: assuming drive cache: write through
[  767.758000]  sda: sda1
[  767.775000] sd 1:0:0:0: Attached scsi disk sda
[  767.775000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[  767.778000] usb-storage: device scan complete

---

### Post by skip27 on 2007-04-21
See, you have exactly the opposite problem I do. Fiesty is automounting my external drive and I don't want that (it's a bit more complicated than that, but anyway...)! Check /etc/udev/rules.d and see if you remember writing any rules. If you don't recall writing any rules, then you'll need to go ahead and write them... or you can use autofs.

[http://72.14.253.104/search?q=cache:K-2WtURkChkJ:www.reactivated.net/udevrules.php+udev+rules&hl=en&ct=clnk&cd=1&gl=us](http://72.14.253.104/search?q=cache:K-2WtURkChkJ:www.reactivated.net/udevrules.php+udev+rules&hl=en&ct=clnk&cd=1&gl=us)

You'll have to use the cached Google version for now, but that's the website that got me started on using udev rules. Once you tell udev to mount the drive, you'll be all set.

---

### Post by katzman on 2007-04-21
sorry but i dont think you understand the problem...it does work with one kernel but not all the others....i don't see how the ude rules would affect this

---

### Post by skip27 on 2007-04-21
No, I think I do: I'm almost willing to bet that you've disabled an option in the kernel that automounting--as you knew it--depended on. So, you can try two things:

1) Write a udev rule. Like I've already stated, udev will work independently of whichever kernel you're using. When I was using Edgy, I compiled my own 2.6.20.4 kernel and my drives still mounted using udev.

2) Recompile the kernel you want using the configuration from the generic kernel (i.e. config-2.6.20-15-generic or whatever it is for you). Don't REMOVE functionality from the kernel; only add the stuff you need. Once you recompile the kernel, update grub, etc. If the drives automount on bootup, then you KNOW it has to do with one of the options in the kernel. If this doesn't work, then I'm stumped.

---

### Post by katzman on 2007-04-21
from your post it sounded like you were trying to blame something having changed in udev for the effect.
So i took your advice and compiling a kernel using the generic config and both of the issue are gone there; that is to say that sb automounts and the hardrives are sda (but this means they do not work with hdparm so i have to disable that)
so you have any idea what kernel conf option causes this....i have been looking but not finding anywthing

---

### Post by skip27 on 2007-04-21
I'm glad to see that my suggestions worked :) I don't know, unfortunately, what causes your external HD to report as a SCSI drive. That type of option is probably at an even lower level, meaning that it may not be configurable even if you are doing a custom rebuild. My external drives have *always* reported as sd#.

As we speak, I'm currently building a custom kernel (2.6.20.7) to see if I can fix my own automounting problems.

Hopefully, perhaps someone can tell you exactly why the drives report as they do.

---

### Post by katzman on 2007-04-21
it is being reported as a scsi dirve,sdb etc THE ONLY thing not working is automounting,manual mount works okay.....trying another kernel see if that one works then if i can figure out what option it was

---

