---
title: "Usb problem"
date: 2008-03-17
forum: General Help
---

### Post by KuriKai on 2008-03-17
Hey.
I have a memory card reader and I had my SD card in there, I had started shutting down ubuntu and while it was shutting down I took out the SD card
And now when I try and plug a usb or SD card into my computer it won't mount.

Does not effect other usb devices like mouse, printer or wacom tablet
here is lsusb without the usb in
```
~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 002 Device 002: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000  

```
And here it is with the usb plugged in
```

lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 002 Device 002: ID 04fc:0561 Sunplus Technology Co., Ltd Flexcam 100
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000  

```
the light on my usb flickers when first plugged in, then it goes out

Any help would be appreciated

---

### Post by PointyWombat on 2008-03-18
Hi,

I don't know the answer, but may be able to help come to one.

First, with the device not plugged in, run:
"cat /proc/mounts", post output.
then, "tail -f /var/log/messages" and plug the device in, post relevant output from this.
then, "cat /proc/mounts" again and post output (if it's different from previous).

---

### Post by KuriKai on 2008-03-18
here is the output of "cat /proc/mounts"
```

cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/disk/by-uuid/b1bcc9ef-3e9b-47dd-be92-4d4e1f94367c / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/b1bcc9ef-3e9b-47dd-be92-4d4e1f94367c /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sdb2 /home ext3 rw,data=ordered 0 0
/dev/sda6 /media/sda6 ext3 rw,data=ordered 0 0
/dev/sda7 /media/sda7 vfat rw,gid=46,fmask=0007,dmask=0007,codepage=cp437,iocharset=iso8859-1,utf8 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev 0 0

```
"tail -f /var/log/messages" result
```

tail -f /var/log/messages
Mar 18 15:56:42 dave-desktop kernel: [ 1482.801551] usb 3-6: new high speed USB device using ehci_hcd and address 60
Mar 18 16:12:48 dave-desktop -- MARK --
Mar 18 16:32:48 dave-desktop -- MARK --
Mar 18 16:52:49 dave-desktop -- MARK --
Mar 18 17:12:49 dave-desktop -- MARK --
Mar 18 17:32:49 dave-desktop -- MARK --
Mar 18 17:52:50 dave-desktop -- MARK --
Mar 18 18:12:50 dave-desktop -- MARK --
Mar 18 18:32:50 dave-desktop -- MARK --
Mar 18 18:52:51 dave-desktop -- MARK --
Mar 18 19:04:48 dave-desktop kernel: [12756.321213] usb 3-3: new high speed USB device using ehci_hcd and address 61
Mar 18 19:04:48 dave-desktop kernel: [12756.864609] usb 3-3: new high speed USB device using ehci_hcd and address 62
Mar 18 19:04:49 dave-desktop kernel: [12757.408025] usb 3-3: new high speed USB device using ehci_hcd and address 63
Mar 18 19:04:49 dave-desktop kernel: [12757.927447] usb 3-3: new high speed USB device using ehci_hcd and address 64
Mar 18 19:04:50 dave-desktop kernel: [12758.446869] usb 3-5: new high speed USB device using ehci_hcd and address 65
Mar 18 19:04:51 dave-desktop kernel: [12758.990275] usb 3-5: new high speed USB device using ehci_hcd and address 66
Mar 18 19:04:51 dave-desktop kernel: [12759.533679] usb 3-5: new high speed USB device using ehci_hcd and address 67
Mar 18 19:04:52 dave-desktop kernel: [12760.053120] usb 3-5: new high speed USB device using ehci_hcd and address 68
Mar 18 19:04:52 dave-desktop kernel: [12760.572541] usb 3-6: new high speed USB device using ehci_hcd and address 69
Mar 18 19:04:53 dave-desktop kernel: [12761.115940] usb 3-6: new high speed USB device using ehci_hcd and address 70
Mar 18 19:04:53 dave-desktop kernel: [12761.659344] usb 3-6: new high speed USB device using ehci_hcd and address 71
Mar 18 19:04:54 dave-desktop kernel: [12762.178777] usb 3-6: new high speed USB device using ehci_hcd and address 72

```
second "cat /proc/mounts" output
```

cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/disk/by-uuid/b1bcc9ef-3e9b-47dd-be92-4d4e1f94367c / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/b1bcc9ef-3e9b-47dd-be92-4d4e1f94367c /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/sdb2 /home ext3 rw,data=ordered 0 0
/dev/sda6 /media/sda6 ext3 rw,data=ordered 0 0
/dev/sda7 /media/sda7 vfat rw,gid=46,fmask=0007,dmask=0007,codepage=cp437,iocharset=iso8859-1,utf8 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
/dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev 0 0

```

---

### Post by PointyWombat on 2008-03-18
Ok, so no difference with /proc/mounts before and after. but the system sees it as per messages.


With the device removed, can you do:

```
ls -la /media
```

then again with device plugged in.

also run:

```
find /proc/scsi -ls
```

before and after.

---

### Post by KuriKai on 2008-03-18
ls -la /media
(without)
```

dave@dave-desktop:~$ ls -la /media
total 62
drwxr-xr-x 13 root root     4096 2008-03-18 15:32 .
drwxr-xr-x 21 root root     4096 2008-02-13 22:26 ..
drwxr-xr-x  2 root root     4096 2008-02-10 21:14 300
lrwxrwxrwx  1 root root        6 2008-01-06 20:07 cdrom -> cdrom0
dr-xr-xr-x  1 root root     2048 2005-01-05 18:08 cdrom0
drwxr-xr-x  2 root root     4096 2008-01-06 20:07 cdrom1
lrwxrwxrwx  1 root root        7 2008-01-06 20:07 floppy -> floppy0
drwxr-xr-x  2 root root     4096 2008-01-06 20:07 floppy0
-rw-r--r--  1 root root        0 2008-03-18 15:32 .hal-mtab
drwxr-xr-x  2 root root     4096 2008-01-21 18:47 IllustratorCS
drwxr-xr-x  2 root root     4096 2008-02-08 14:20 phonebooth
drwxr-xr-x  2 root root     4096 2008-01-16 22:21 PortableAdobeCollection
drwxr-xr-x  2 root root     4096 2008-02-15 13:27 RCTYCOON
drwxrwx--- 20 root plugdev  4096 2008-03-17 00:48 sda6
drwxrwx---  8 root plugdev 16384 1970-01-01 12:00 sda7
drwxr-xr-x  2 root root     4096 2008-01-07 15:52 war3tft

```
with
```

dave@dave-desktop:~$ ls -la /media
total 62
drwxr-xr-x 13 root root     4096 2008-03-18 15:32 .
drwxr-xr-x 21 root root     4096 2008-02-13 22:26 ..
drwxr-xr-x  2 root root     4096 2008-02-10 21:14 300
lrwxrwxrwx  1 root root        6 2008-01-06 20:07 cdrom -> cdrom0
dr-xr-xr-x  1 root root     2048 2005-01-05 18:08 cdrom0
drwxr-xr-x  2 root root     4096 2008-01-06 20:07 cdrom1
lrwxrwxrwx  1 root root        7 2008-01-06 20:07 floppy -> floppy0
drwxr-xr-x  2 root root     4096 2008-01-06 20:07 floppy0
-rw-r--r--  1 root root        0 2008-03-18 15:32 .hal-mtab
drwxr-xr-x  2 root root     4096 2008-01-21 18:47 IllustratorCS
drwxr-xr-x  2 root root     4096 2008-02-08 14:20 phonebooth
drwxr-xr-x  2 root root     4096 2008-01-16 22:21 PortableAdobeCollection
drwxr-xr-x  2 root root     4096 2008-02-15 13:27 RCTYCOON
drwxrwx--- 20 root plugdev  4096 2008-03-17 00:48 sda6
drwxrwx---  8 root plugdev 16384 1970-01-01 12:00 sda7
drwxr-xr-x  2 root root     4096 2008-01-07 15:52 war3tft

```

 find /proc/scsi -ls
without
```

dave@dave-desktop:~$ find /proc/scsi -ls
4026532004    0 dr-xr-xr-x   3 root     root            0 Mar 18 22:14 /proc/scsi
4026532013    0 dr-xr-xr-x   2 root     root            0 Mar 18 22:14 /proc/scsi/sg
4026532020    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/version
4026532019    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/device_strs
4026532018    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/devices
4026532017    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/device_hdr
4026532016    0 -rw-r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/def_reserved_size
4026532015    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/debug
4026532014    0 -rw-r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/allow_dio
4026532006    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/device_info
4026532005    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/scsi

```
with
```

dave@dave-desktop:~$ find /proc/scsi -ls
4026532004    0 dr-xr-xr-x   3 root     root            0 Mar 18 22:14 /proc/scsi
4026532013    0 dr-xr-xr-x   2 root     root            0 Mar 18 22:14 /proc/scsi/sg
4026532020    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/version
4026532019    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/device_strs
4026532018    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/devices
4026532017    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/device_hdr
4026532016    0 -rw-r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/def_reserved_size
4026532015    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/debug
4026532014    0 -rw-r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/sg/allow_dio
4026532006    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/device_info
4026532005    0 -r--r--r--   1 root     root            0 Mar 18 22:14 /proc/scsi/scsi

```

---

### Post by KuriKai on 2008-03-20
bump^^

I really don't want to have to reinstall ubuntu

---

### Post by KuriKai on 2008-03-20
Nevermind, I fixed it.

All I had to do was turn of the computer and then unplug it from the wall, then plug it back in and turn it on.

thanks for the help

---

