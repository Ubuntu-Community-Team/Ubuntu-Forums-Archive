---
title: "Downgrading the kernel"
date: 2006-08-04
forum: General Help
---

### Post by george_apan on 2006-08-04
I have a pcmcia USB controller card that doesn't work right in Dapper. And not only Dapper, but in any other distribution with a recent kernel that I've tried. With Breezy everything worked with kernels 2.6.12 but when I compiled a recent kernel for breezy (with the same config) it didn't work again. So I figure this is a bug in more recent versions of the kernel.

So, is it possible to downgrade the Dapper kernel to version 2.6.12? If so, are there going to be any big problems? I'm thinking the udev thing might be an issue...

---

### Post by george_apan on 2006-08-05
bump...

---

### Post by mlind on 2006-08-05
Have you tried downloading breezy kernel (linux-source-2.6) package from breezy repository and compile that one?
If you suspect that it's a udev problem, it's not kernel's fault. You can create new udev rule for your USB controller.

Can you find udev information for your USB device using
```

for i in /sys/bus/usb/devices/*; do udevinfo -a -p $i; done

```

---

### Post by george_apan on 2006-08-05
> **mlind said:**
> Have you tried downloading breezy kernel (linux-source-2.6) package from breezy repository and compile that one?
That's what I'm going to try next.
edit: But I know that if I compile a recent kernel for breezy I get the same behaviour as in dapper.

> **mlind said:**
> If you suspect that it's a udev problem, it's not kernel's fault. You can create new udev rule for your USB controller.

Can you find udev information for your USB device using
```

for i in /sys/bus/usb/devices/*; do udevinfo -a -p $i; done

```
I have no idea how to create udev rules. The problem could be kernel or udev related. All I know is that in breezy everything worked OK. The output of the above command follows in the next reply because it's too big.

Thank you for your time mlind.

---

### Post by george_apan on 2006-08-05
I created an attachment because the output was still too big for a post. Here it is: [http://www.ubuntuforums.org/attachment.php?attachmentid=13846&stc=1&d=1154791769](http://www.ubuntuforums.org/attachment.php?attachmentid=13846&stc=1&d=1154791769)

---

### Post by mlind on 2006-08-05
> **george_apan said:**
> I created an attachment because the output was still too big for a post. Here it is: [http://www.ubuntuforums.org/attachment.php?attachmentid=13846&stc=1&d=1154791769](http://www.ubuntuforums.org/attachment.php?attachmentid=13846&stc=1&d=1154791769)

That attachment doesn't work. You could use gzip to pack the file is it's too big to attach.

I'll help you making a udev rule for your device. This is good tutorial that covers the steps [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by george_apan on 2006-08-05
> **mlind said:**
> That attachment doesn't work. You could use gzip to pack the file is it's too big to attach.
Are you sure? It works fine for me. Just do a 'gunzip udev.txt.gz'.

> **mlind said:**
> I'll help you making a udev rule for your device. This is good tutorial that covers the steps [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)
I'm not sure this will help. As I said before this problem also happens with a recent kernel and breezy. The PCMCIA card itself is recognized and seems to be working but I cannot mount my external hard drive on it. If I attach it, CPU hits 100%, the system freezes after a while and I can't do anything, not even shutdown. And I get no error with dmesg in the process. Is it possible that this is a udev problem? Should I try this before trying a previous kernel version?

---

### Post by mlind on 2006-08-05
> **george_apan said:**
> Are you sure? It works fine for me. Just do a 'gunzip udev.txt.gz'.


When i click the link I just get "Invalid Attachment specified. If you followed a valid link, please notify the administrator" :confused: 

> **george_apan said:**
> 
I'm not sure this will help. As I said before this problem also happens with a recent kernel and breezy. The PCMCIA card itself is recognized and seems to be working but I cannot mount my external hard drive on it. If I attach it, CPU hits 100%, the system freezes after a while and I can't do anything, not even shutdown. And I get no error with dmesg in the process. Is it possible that this is a udev problem? Should I try this before trying a previous kernel version?

Can you see what process starts eating your cpu? pmount?

---

### Post by george_apan on 2006-08-05
> **mlind said:**
> When i click the link I just get "Invalid Attachment specified. If you followed a valid link, please notify the administrator" :confused: 
Don't know why that happens. I've also uploaded it here: [http://www.mytempdir.com/849085](http://www.mytempdir.com/849085)

> **mlind said:**
> Can you see what process starts eating your cpu? pmount?
I don't remember right now. I will post that in a while when I get back to that pc.

---

### Post by george_apan on 2006-08-05
OK I've checked and I can't find which process it is. Running the top command on a terminal displays no process with high CPU utilisation but when I hover the mouse in the gnome-panel applet it shows that 100% is used. That said it is not a foreground task that is using the CPU. The background is getting a bit brighter, which I think shows that a background task consumes the CPU.

What I get with dmesg is this:
```
[4294979.178000] usb 5-1.2: new high speed USB device using ehci_hcd and address  5
[4294979.256000] scsi1 : SCSI emulation for USB Mass Storage devices
[4294979.256000] usb-storage: device found at 5
[4294979.256000] usb-storage: waiting for device to settle before scanning
[4294984.258000]   Vendor: Maxtor 7  Model: Y250P0            Rev: 0811
[4294984.258000]   Type:   Direct-Access                      ANSI SCSI revision : 00
[4294984.258000]  1:0:0:0: Attached scsi generic sg1 type 0
[4294984.266000] usb-storage: device scan complete
[4294984.339000] Driver 'sd' needs updating - please use bus_type methods
[4294984.436000] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[4294984.437000] sda: assuming drive cache: write through
[4294984.478000] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[4294984.478000] sda: assuming drive cache: write through
[4294984.478000]  sda: sda1
[4294984.550000] sd 1:0:0:0: Attached scsi disk sda
[4294987.930000] ReiserFS: sda1: found reiserfs format "3.6" with standard journ al
[4295003.676000] ReiserFS: sda1: using ordered data mode
[4295003.699000] ReiserFS: sda1: journal params: device sda1, size 8192, journal  first block 18, max trans len 1024, max batch 900, max commit age 30, max trans  age 30
[4295003.707000] ReiserFS: sda1: checking transaction log (sda1)
```
Everything seems normal but nothing gets mounted.

---

### Post by mlind on 2006-08-06
> **george_apan said:**
> OK I've checked and I can't find which process it is. Running the top command on a terminal displays no process with high CPU utilisation but when I hover the mouse in the gnome-panel applet it shows that 100% is used. That said it is not a foreground task that is using the CPU. The background is getting a bit brighter, which I think shows that a background task consumes the CPU.


Try with gnome-system-monitor instead. Be sure to select "All processes" from View menu, and activate "% CPU" from Preferences > Processes.
I didn't have any luck downloading your attachment this time either. firefox times out with error "Firefox can't find the server at sr2.mytempdir.com" ..

---

### Post by george_apan on 2006-08-06
It's all the same. Even with "All processes" selected in gnome-system-monitor none shows as using the CPU but the CPU is always at 100%! And I also get this if they are any helpful:
```
PROCESS    STATUS           %CPU   ARGUMENTS
mount      Uninterruptible  0      /bin/mount -t reiserfs -o nodev,noauto,nosuid,user,async,atime,exec /dev/sda1 /media/usbdisk
pmount     Sleeping         0      pmount -t reiserfs --exec /dev/sda1 usbdisk
pmount-hal Sleeping         0      /usr/bin/pmount-hal /org/freedesktop/Hal/devices/volume_uuid_some-numbers-here
```

About the attachment, I don't know what to do next, both work here for 3 different PCs. Could you pm me you e-mail so I can send it to you?

---

### Post by george_apan on 2006-08-08
OK, this is definately not a problem with udev or pcmcia. It is a problem with the ehci_hcd kernel module. If I do 'modprobe -r ehci_hcd', my hard drive mounts on the pcmcia ports but ofcource only as usb 1.0 "full speed" and not as a usb 2.0 high speed device. This means it is really slow. Something changed in ehci_hcd from the 2.6.12 kernel that breezy uses to dapper's kernel that created this mess. Is there any other usb 2.0 driver I can try or am I stuck with either breezy or USB 1.0 speeds? Or does anyone know what changed in the module?

---

