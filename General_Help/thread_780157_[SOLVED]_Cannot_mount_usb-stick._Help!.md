---
title: "[SOLVED] Cannot mount usb-stick. Help!"
date: 2008-05-03
forum: General Help
---

### Post by piter345 on 2008-05-03
Hello!

I've just installed Xubuntu 8.04 but cannot get it to mount my usb-stick..

The story so far: previously I used Kubuntu 5.10 which was perfectly able to automount my stick after I had added an entry in /etc/fstab listing the usb-device at /dev/sda1. At that time my hard drive was listed in /etc/fstab as /dev/hda?.

Xubuntu 8.04, however, recognized my hard-disk as /dev/sda (don't ask me why, I don't have any SCSI-stuff). I'm having 3 partitions (dev/sda1-3). Now, the /dev/sda1 is already taken. So, what should I enter in /etc/fstab instead?

I read part of the very good posting regarding the fstab and how to indicate a filesystem not by its dev-name but rather by label or uuid. 

My problem at this point: /dev/disk doesn't contain a sub-directory "by-label". It only contains the sub-dirs by-id, by-path and by-uuid.

I attached the usb-stick, and voila inside by-id there appeared the device "usb-USB_2.0_Flash_Drive-0:0". Unfortunately one cannot indicate the device by it's "id". One has to use either "label" or "uuid". So I had a look at the directory "by-uuid". However, there I found no indication of my usb-stick, only the uuid's of my hard disk.

At this point, the only thing I can say is: Help!

Piter

---

### Post by chrisccoulson on 2008-05-03
I think you're over-complicating things a bit. Your USB stick should automaticaly mount, and shouldn't need an entry in /etc/fstab. Try removing the entry.

FSTAB is primarily for static filesystems

---

### Post by mali2297 on 2008-05-03
I think it's now placed at **/dev/sdb1**.

After connecting the device, check
```

dmesg | tail

```
On my system, I then see
```

[  654.792646]  sdb: sdb1
[  654.794379] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  654.794475] sd 3:0:0:0: Attached scsi generic sg2 type 0

```
The usb stick also gets automatically detected in Thunar even though I don't have a volume manager installed.

---

### Post by piter345 on 2008-05-03
Hello Chris!
Hello Martin!

Thanks for your replies. The bit about "dmesg" was especially enlightening. The command provided the following output:

```

[ 1194.713826] scsi2 : SCSI emulation for USB Mass Storage devices
[ 1194.725693] usbcore: registered new interface driver usb-storage
[ 1194.728661] USB Mass Storage support registered.
[ 1194.731558] usb-storage: device found at 3
[ 1194.731572] usb-storage: waiting for device to settle before scanning
[ 1199.730298] usb-storage: device scan complete
[ 1199.733643] scsi scan: INQUIRY result too short (5), using 36
[ 1199.733660] scsi 2:0:0:0: Direct-Access     USB      2.0 Flash Drive  1.00 PQ: 0 ANSI: 0
[ 1199.748756] sd 2:0:0:0: [sdb] Attached SCSI disk
[ 1199.748862] sd 2:0:0:0: Attached scsi generic sg3 type 0

```

So, Linux indeed seems to know about the USB-stick. However, I was unable to find out how to mount it. I added the following line to /etc/fstab:

> 
/dev/sdb1     /media/usbdisk  vfat rw,noexec,nodev,quiet,uid=1000,gid=1000,umask=077


When I ran "sudo mount /media/usbdisk" I was greeted with the error message "device file /dev/sdb1 doesn't exist" (or something like that, my error message is in German). 

Afterwards I commented this line out. When I reran the mount-command I got the error message "Couldn't find /media/usbdisk in /etc/fstab or /etc/mtab". No surprise there. I guess that I have to manually create /dev/sdb and /dev/sdb1. But how? I would be grateful for any suggestions.

Bye,

Piter

---

### Post by mali2297 on 2008-05-03
The "file" /dev/sdb1 is created at the moment as the usb device is attached, I don't think that you should make one yourself.

After that you have attached the usb stick, check if you can mount it with
```

mount /dev/sdb1 /media/usbdisk

```
or
```

mount /dev/sdb /media/usbdisk

```

---

### Post by chrisccoulson on 2008-05-03
Indeed, /dev/sdb1 will be created by UDEV on insertion of the USB stick, and then the volume should get automounted. If it's not being created, this is either because there are no filesystems on the stick, or some other kernel issue. You can't create it manually, and you shouldn't need to specify the device in your /etc/fstab.

With the device plugged in, what is the output of:
```
sudo fdisk -l /dev/sdb
```

Googling reveals lots of problems with the ehci_hcd module and USB2 storage devices. See this for example: [http://www.fedoraforum.org/forum/showthread.php?t=160151]("http://www.fedoraforum.org/forum/showthread.php?t=160151")

If fdisk doesn't return a valid partition table, try unloading the ehci_hcd module to see if you have the same issue.

---

### Post by piter345 on 2008-05-05
Hello Chris!

Many thanks for your help. I really appreciate it. I tried out the "sudo fdisk -l /dev/sdc"-command (/dev/sdc because I just installed a second hard disk) with my problematic USB-stick attached. No success. The command doesn't print out a single line.

The file "/proc/modules" lists the following modules which might be relevant to USB:

- usbcore 146028 4 usb_storage,libusual,uhci_hcd, Live 0xd88e0000
- scsi_mod 151436 5 usb_storage,sg,sr_mod,sd_mod,libata, Live 0xd8892000

I did a "sudo rmmod uhci_hcd", reattached the usb-stick. Result: nil. So reloaded the module with "sudo modprobe uhci_hcd", reattached the usb-stick. Result (dmesg | tail):

```
[ 4707.295670] usb 1-2.1: new full speed USB device using uhci_hcd and address 5
[ 4707.435741] usb 1-2.1: configuration #1 chosen from 1 choice
[ 4707.464117] scsi12 : SCSI emulation for USB Mass Storage devices
[ 4707.467806] usb-storage: device found at 5
[ 4707.467818] usb-storage: waiting for device to settle before scanning
[ 4712.464374] usb-storage: device scan complete
[ 4712.467360] scsi scan: INQUIRY result too short (5), using 36
[ 4712.467379] scsi 12:0:0:0: Direct-Access     USB      2.0 Flash Drive  1.00 PQ: 0 ANSI: 0
[ 4712.484454] sd 12:0:0:0: [sdc] Attached SCSI disk
[ 4712.484564] sd 12:0:0:0: Attached scsi generic sg4 type 0
```

Next, I again removed the uhci_hcd-module and instead loaded ehci_hcd-module. Result: nothing at all. So I re-instated uhci_hcd.

Now I tried out a different usb-stick. Funny enough, this one worked. It was recognized AND automatically mounted, an icon placed on the desktop and Thunar opened. After attaching this USB-stick "dmesg | tail" gave the following output:

```
[ 3009.754758] usb 1-2: new full speed USB device using uhci_hcd and address 10
[ 3009.922897] usb 1-2: configuration #1 chosen from 1 choice
[ 3009.987344] scsi7 : SCSI emulation for USB Mass Storage devices
[ 3009.991145] usb-storage: device found at 10
[ 3009.991158] usb-storage: waiting for device to settle before scanning
[ 3014.989518] usb-storage: device scan complete
[ 3014.992511] scsi 7:0:0:0: Direct-Access     CBM      Flash Disk       4.00 PQ: 0 ANSI: 2
[ 3014.998506] sd 7:0:0:0: [sdc] 498687 2048-byte hardware sectors (1021 MB)
[ 3015.001449] sd 7:0:0:0: [sdc] Write Protect is off
[ 3015.001466] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 3015.001472] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 3015.010424] sd 7:0:0:0: [sdc] 498687 2048-byte hardware sectors (1021 MB)
[ 3015.013461] sd 7:0:0:0: [sdc] Write Protect is off
[ 3015.013475] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 3015.013481] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 3015.013495]  sdc: unknown partition table
[ 3015.038526] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 3015.038642] sd 7:0:0:0: Attached scsi generic sg4 type 0
```

The problem seems to lie in a difference between the two USB-sticks, the one which is not working is a "Diamond Drive 256 MB USB 2.0". The one working, I don't know anything about it (except its size of 2 GB of which only 1 GB is available for some reason), because it was given out by a company. However, I have to emphasize that the 256 MB is not faulty. I can use it inside Windows, and I can (still) use it from inside the Ubuntu 5.10 Live-CD.

H E L P ! I am my wits' end. I even was so desperate to "sudo MAKEDEV sdc". It did create device nodes like /dev/.static/dev/sdc1 etc, but my 256-stick still doesn't work.

Any suggestions?

Piter

---

### Post by piter345 on 2008-06-09
Hello!

I just bought a new computer with fairly up-to-date hardware (Intel dual core, Nvidia 8600, two 250GB-Western Digital disks). And everything is working fine. Installation was a breeze (to muy great surprise, actually).

The 256MB-memory stick still doesn't work, but that doesn't matter. It's too small anyway. I'm going to chuck it. I do still wonder why it didn't work. I guess Ubuntu regarding my hard disks as scsi-devices (/dev/sd* instead of /dev/hd*) was at least part of the problem. But nevermind. That's behind me.

So, this thread is "solved" (in a way, at least).

Still, thanks a lot for your help.

Over and out,

Piter

---

