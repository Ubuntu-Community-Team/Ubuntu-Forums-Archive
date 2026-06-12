---
title: "USB flash drive will not mount"
date: 2007-03-16
forum: General Help
---

### Post by fracktor on 2007-03-16
I am unable to get my USB flash drive to mount on Ubuntu Edgy. I have two usb flash drives and neither one will mount. They both work fine on a windows xp box. Below is the output after plugging in the drive....
 fracktor@eternity:~$ tail -n 0 -f /var/log/messages
Mar 16 18:22:52 eternity kernel: [17180126.404000] usb 4-4: new high speed USB device using ehci_hcd and address 4


-then nothing else happens. 

If I try lsusb it just hangs there forever and does nothing.

Any help is greatly appreciated.

---

### Post by mrmonday on 2007-03-17
With one of your drives plugged in, what is the output of
```
fdisk -l
```

---

### Post by fracktor on 2007-03-17
fracktor@eternity:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30213   242685891   83  Linux
/dev/hda2           30214       30401     1510110    5  Extended
/dev/hda5           30214       30401     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+   7  HPFS/NTFS

---

### Post by fracktor on 2007-03-17
I don't even see it listed with that output. Also, another thing, I can plug in my digital camera via USB and it works fine, and I can also charge my cell phone via USB. I don't understand why its not picking up the flash drives.

---

### Post by mrmonday on 2007-03-18
If you right click on your panel, go to add to panel, then select drive mounter, is your flash drive listed?

---

### Post by fracktor on 2007-03-18
If you right click on your panel, go to add to panel, then select drive mounter, is your flash drive listed? 

No, its not listed. 

I have also tried other usb ports and if I switch to xp they work fine.

---

### Post by fracktor on 2007-03-19
anyone else have any ideas...

---

### Post by DrOlaf on 2007-03-19
What format are these flash drives?

---

### Post by Unaha-Closp on 2007-03-20
I had the same problem on dapper with my mp3 player, as have others. They used the following command, after first unpluging usb devices,

sudo modprobe -r ehci_hcd

and then pluging them back in. I worked for me, I've no idea of the whys and wherefores :confused: , but give it ago. (It looks like you need to do this every time you reboot.)

---

### Post by fracktor on 2007-03-21
What format are these flash drives?
they are FAT formatted

I had the same problem on dapper with my mp3 player, as have others. They used the following command, after first unpluging usb devices,
sudo modprobe -r ehci_hcd

That worked! I am able to browse the flash drive now! What does that do exactly? sudo modprobe -r ehci_hcd

---

### Post by DrOlaf on 2007-03-21
ehci_hcd is a driver for USB2 devices. The modprobe command is used to load, and unload, modules from the kernel. Using it with the -r switch removes a module. So, you have removed the ehci_hcd module from the kernel. 

This does seem to be a recognized bug in Ubuntu:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/54419)

---

