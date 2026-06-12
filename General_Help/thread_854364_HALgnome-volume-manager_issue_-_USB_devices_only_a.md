---
title: "HAL/gnome-volume-manager issue - USB devices only appear if connected at boot"
date: 2008-07-09
forum: General Help
---

### Post by Kimos on 2008-07-09
I've been having a problem with USB devices on my 8.04 x86 desktop. My printer, iPod, external HD, and digital camera all work properly if they are connected when the system powers up. If I plug in my iPod, I have to restart X with it plugged in to get it to mount.

Before I fully understood how big this problem was, I got my Canon camera working by creating "/etc/udev/rules.d/45-libgphoto2.rules" and putting in a line like:

```
SYSFS{idVendor}=="04a9", SYSFS{idProduct}=="314c", MODE="0660", GROUP="plugdev"
```

I do not understand what that does, other than the first two numbers are specific to my camera/model.

When I plug in the iPod I get this appearing in dmesg:

```
[485589.765193] usb 5-2: new high speed USB device using ehci_hcd and address 8
[485589.898837] usb 5-2: configuration #1 chosen from 2 choices
[485589.929566] scsi8 : SCSI emulation for USB Mass Storage devices
[485589.937066] usb-storage: device found at 8
[485589.937073] usb-storage: waiting for device to settle before scanning
[485594.927777] usb-storage: device scan complete
[485594.930623] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[485594.945960] sd 8:0:0:0: [sdd] 1982464 2048-byte hardware sectors (4060 MB)
[485594.947052] sd 8:0:0:0: [sdd] Write Protect is off
[485594.947063] sd 8:0:0:0: [sdd] Mode Sense: 68 00 00 08
[485594.947066] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[485594.949497] sd 8:0:0:0: [sdd] 1982464 2048-byte hardware sectors (4060 MB)
[485594.950447] sd 8:0:0:0: [sdd] Write Protect is off
[485594.950452] sd 8:0:0:0: [sdd] Mode Sense: 68 00 00 08
[485594.950454] sd 8:0:0:0: [sdd] Assuming drive cache: write through
[485594.950461]  sdd: sdd1 sdd2
[485594.954111] sd 8:0:0:0: [sdd] Attached SCSI removable disk
[485594.954162] sd 8:0:0:0: Attached scsi generic sg5 type 0
```

No errors from what I understand, but it does not mount on the desktop and Amarok does not see it. Trying to mount /etc/sdd2 from the command line does not work. 

The only thread I've been able to locate with a similar problem is this one:

[http://ubuntuforums.org/showthread.php?t=333476](http://ubuntuforums.org/showthread.php?t=333476)

I have confirmed that I have gnome-volume-manager --sm-disable in my session startup, and executing it from the command line does not change anything.

I installed ivman (blindly) and got some very strange behavior so I removed it.

I'm looking for suggestions. Things to change. Even things to remove/purge and re-install. I have a very vague understanding of HAL and how USB devices are managed. I know this all worked properly to begin with, but some kind of update or change broke it.

---

### Post by Kimos on 2008-07-16
After some serious searching and digging I found a thread that could help me:

[http://ubuntuforums.org/showthread.php?t=582045](http://ubuntuforums.org/showthread.php?t=582045)

Here's the related bug report:

[https://bugs.launchpad.net/ubuntu/+bug/211760](https://bugs.launchpad.net/ubuntu/+bug/211760)

There are a few proposed solutions in that thread, but what worked for me was reinstalling part of HAL:

```
sudo aptitude reinstall libhal1 libhal-storage1
```

---

