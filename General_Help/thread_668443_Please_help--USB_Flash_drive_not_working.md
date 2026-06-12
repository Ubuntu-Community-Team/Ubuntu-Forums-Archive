---
title: "Please help--USB Flash drive not working"
date: 2008-01-15
forum: General Help
---

### Post by miqie on 2008-01-15
I have two USB flash drives that work fine in Windows but are not seen in Gutsy. I am using a dual boot WindowsXP/Ubuntu computer, so I know that the USB ports work. Why doesn't Ubuntu see the drives and whats the fix? They are a Kingston Data Traveler 1GB and an Eagletec 128mb.
Here is the output from the terminal window:

Bus 001 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

I have a USB mouse plugged in, which is working and an old Visioneer Onetouch scanner which is not detected by Xsane.
One thing that did come up right before the login screen was a checklist of what was loading. I noticed 3 lines:

USB 5-5 device not accepting address 5 error-110
USB 5-5 device not accepting address 6 error-110
USB 5-5 device not accepting address 7 error-110

then it went to the login screen.  Also, yesterday I loaded "USB View" thinking maybe it could help. When I put the stick in and open this application I get the message: "Cannot open the file /proc/bus/usb/devices" and then it says: "Verify that you have USB compiled into your kernel, have the USB core modules loaded, and have the usbdevfs filesystem mounted." Does this provide any clues to my problem?  The flash drives also do not work when running Gutsy from the live CD.

---

### Post by Nexusx6 on 2008-01-15
Unplug the USB for a few seconds, then plug it back in and in a terminal session type:
```
dmesg | tail
```
and post the results

---

### Post by miqie on 2008-01-15
Please note that when I plug the flash drive in, the stick's LED doesn't even blink, like it does in Windows.  It's like the port isn't even trying to read the drive.  I know that the drive and port work because when I boot to Windows XP they work fine.  Here is the output from terminal: 

mike@mike-desktop:~$ dmesg | tail
[  429.031811]  [<c011dba2>] native_safe_halt+0x2/0x10
[  429.031822]  [<c0102e3c>] default_idle+0x3c/0x60
[  429.031826]  [<c0102413>] cpu_idle+0x53/0xe0
[  429.031842]  [<c03e3a85>] start_kernel+0x325/0x3b0
[  429.031852]  [<c03e31f0>] unknown_bootoption+0x0/0x260
[  429.031881]  =======================
[  429.031883] handlers:
[  429.031885] [<e087a6a0>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  429.031912] [<e08a3b20>] (rhine_interrupt+0x0/0xb70 [via_rhine])
[  429.031923] Disabling IRQ #12

---

### Post by davesmith on 2008-01-15
you need to mount the drive so that Ubuntu sees it

could you plug it in and post the output of

<sudo fdisk -l>

---

### Post by miqie on 2008-01-15
As you can see, the flashdrive doesn't even show up, just my harddrives. As stated before, the LED doesn't light up when I plug it in.  It does in Windows, however.  

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10e510e4

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1944    15615148+   c  W95 FAT32 (LBA)
/dev/hda2            1945        7476    44435790    f  W95 Ext'd (LBA)
/dev/hda5            1945        7476    44435758+   b  W95 FAT32

Disk /dev/hdb: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x729cb918

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         608     4883728+  83  Linux
/dev/hdb2            2402        2498      779152+  82  Linux swap / Solaris
/dev/hdb3             609        2401    14402272+   b  W95 FAT32

Partition table entries are not in disk order

---

### Post by miqie on 2008-01-16
This is my Fstab file.  Shouldn't there be something in there relating to USB's? If so, what modifications do I make to automount my USB flash drive?

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=26642c34-0a7e-4757-a08a-8af631257b3a / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda1 :
UUID=0C54-19F1 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hda5 :
UUID=143F-1A01 /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hdb3 :
UUID=A8A8-C290 /media/hdb3 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/hdb2 :
UUID=30b78780-08dc-4764-903e-36a9ecd6ab28 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

---

### Post by freddyp on 2008-01-16
I'm running 7.10 so not sure if this applies to your version.  And not to insult, but have you checked:

System>Preferences>Storage Tab and made sure the following is checked:

Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

Don't ask me how I know how easy it is to accidentally uncheck one. This should ensure that the USB drive is being recognized by Ubuntu on insert, but remember if you don't ask the O/S to automount it, then it won't be automounted.

---

### Post by miqie on 2008-01-17
Yes they are checked.  That is one of the first things I looked at.  There must be some setting that is causing this.  I suspect its in the fstab file, but i don't know what to change there, and the search on here did not produce any answers. When I plug the stick in, its just dead, but works fine in Windows XP.

---

### Post by miqie on 2008-01-22
I,m still having  problems getting my flash drive to work.  Anymore suggestions?

---

### Post by kainalu on 2008-02-08
i have the same problem

---

### Post by karlrhs on 2008-02-27
I have the same problem.  You are not privileged to mount this volume.

---

