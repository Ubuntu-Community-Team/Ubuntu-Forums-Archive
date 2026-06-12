---
title: "Help - usb pen permissions"
date: 2008-06-21
forum: General Help
---

### Post by ruipedroca on 2008-06-21
Hi,

I've been messing around my usb pen settings and now a funny thing happens:
-when i power on my computer, i can access my usb pen, but i can't write to it
-however, if i safely remove it, unplug it and then plug it again, i'm able to write to it this time
This is anoying for obvious reasons.

Can someone please point me the solution so i can write to it every time without having to unplug it and then plug it again?


Regards

---

### Post by -grubby on 2008-06-22
What exactly did you edit in the USB Drives settings? You should revert them. If that doesn't work, my only other guess would be to reformat the flash drive

---

### Post by ddales on 2008-06-22
If it's plugged in while your PC boots, it's probably being mounted by root at boot time.  If you replug it, it mounts under your session and user so you can write to it.

What you can do is change the permissions in your udev rules definitions, or just plug it in when you need it, or create an fstab entry with the users attribute to mount it at boot with user write permissions.

If you mount it through the fstab though, you'll have to unmount it before you remove it.

---

### Post by ruipedroca on 2008-06-24
Hi,

I can't revert the settings because now i don't know what they were...

I'm going to try ddales's advices and them post feedback!


Regards

---

### Post by ruipedroca on 2008-06-24
Hi,

Udev seems to difficult to me to learn about  right know.

In my fstab, the line regarding my usb pen is this:
/dev/sdd1 /mnt/usb4gb auto users,utf8,atime,auto,rw,dev,exec,suid 0 0

Can somebody please correct it?


Thanks in advance!

---

### Post by ruipedroca on 2008-06-28
Hey guys!

C'mon, just give a help here, please! 
Just take a look at your line in /etc/fstab and post it here so i can see the differences between mine:
/dev/sdd1 /mnt/usb4gb auto users,utf8,atime,auto,rw,dev,exec,suid 0 0

I've tried with udev, but it's too much complicated to my knowledge.

Regards

---

### Post by mc4man on 2008-06-28
First there should be no problem booting up with a pen drive inserted,(unless your bios objects). I do it on both kubuntu and ubuntu. I have 3 usb pen drives and none are in fstab and there's no reason that they should be. One (a sandisk micro cruzer 4gb) does get an entry in /etc/udev/rules.d/70-persistent-cd.rules but that's of no great importance. ( i think it does because it has orig. sandisk formatting so it's seen as both a drive and a removable mass storage device)

Did you have the drive connected when you installed kubuntu? That probably wouldn't have been a great idea.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb3
UUID=cee716b0-112d-4d1e-9b37-f1ef36c90ad3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=3023a85b-b8cd-4d79-ac05-ba357bca3091 /home           ext3    relatime        0       2
# /dev/sda5
UUID=a6b48647-b3cd-4e76-9a83-f912dbd503c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
```
 This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVDR_PX-716AL (pci-0000:00:1f.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DVD_DD_DW1640 (pci-0000:00:1f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
# U3_Cruzer_Micro (pci-0000:00:1d.7-usb-0:8:1.0-scsi-0:0:0:1)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="SanDisk_U3_Cruzer_Micro_00001779A96170ED-0:1", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="SanDisk_U3_Cruzer_Micro_00001779A96170ED-0:1", SYMLINK+="cdrw2", ENV{GENERATED}="1"
```

---

