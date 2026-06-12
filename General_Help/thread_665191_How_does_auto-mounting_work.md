---
title: "How does auto-mounting work?"
date: 2008-01-12
forum: General Help
---

### Post by chandru.in on 2008-01-12
Hi,

In Ubuntu, when I plugg in USB disks, it gets mounted automatically.  How exactly does this work?  What is the sequence of actions taking place?  Where is the configuration to manage this present?

---

### Post by Rocket2DMn on 2008-01-12
If you plug in a USB disk, then run "dmesg" in terminal it will give you an idea of what is happening.  Basically, a new USB device is seen, the computer recognizes it as a drive, and mounts it using default mount options (I believe).  These options vary depending on the filesystem on the drive.
I think in order to modify the mount options for a specific device, you would have to put an entry in /etc/fstab for it and mount it manually when you plug it in (since devices declared in /etc/fstab don't tend to automount unless they are there at computer boot time).

---

### Post by chandru.in on 2008-01-12
No buddy.  fstab entry was necessary in older versions of Linux I remember doing it in Slackware.

But on Ubuntu, it creates a directory automatically in /media and mounts it there.  When unmounted, the directory disappears automatically.

I just want to understand the mechanism behind this.  Also, how can I do the same thing from commandline as a normal user without editing /etc/fstab?  I mean if GUI allows mounting USB by normal user, it should be possible from commandline too.  So how can I do it?

---

### Post by Rocket2DMn on 2008-01-12
You can still have entries in fstab for removable disks.  Trust me, I've done it.  However, when they are in fstab (hence requiring the directory in /media or /mnt to already exist), they will not automount.  When automounting, the directory is temporarily created as you said, and disappears when you unmount.
You can still mount from the command line using the "mount" command, but it will require you to create the mount directory in advance.  So for example, you have an external ntfs drive (assuming you have ntfs-3g installed and configured):
```
sudo mkdir /media/ntfs_external
sudo mount -t ntfs-3g /dev/sdb1 /media/ntfs_external
```
If you have an entry in fstab and the directory already existed, you could just do ***one*** of the following.  I will use device sdb1 for the example.
```
sudo mount -a (this assumes "noauto" is not used)
sudo mount /dev/sdb1
sudo mount /media/ntfs_external
```
Again, if your drive is ntfs and you are looking to mount at a specific directory name under /media rather than just /media/disk , you can download and install ntfsprogs and use "ntfslabel" to specify a name for the device and it will mount using that name under /media .
Please post back any specifics like the contents of fstab and the output of "sudo fdisk -l" if you would like me to help you with your drive.

---

### Post by chandru.in on 2008-01-12
Thanks for the efforts you took to explain.  I know that putting entries in fstab will work.

What I want to know is how does the dynamic automounting in Ubuntu work?  Also, how can a normal user (without sudo permissions) mount a USB key in an automatically created directory under /media from the commandline/terminal, just as Gnome/KDE do it from the GUI?

---

### Post by Rocket2DMn on 2008-01-12
Normally if you plug in a USB flash drive it will automount to something like /media/disk and normal users can access it just fine.  However, when you try to use "mount" from the command line, it will tell you that only root can do that.
However, there is a program called "pmount" which will allow you to mount from command line without root privileges - if it's not already installed, it's in the repositories.  Let's assume fdisk -l says the drive is at sdb1 again.  Note the absence of sudo on both commands.
```
fdisk -l
pmount /dev/sdb1
```
The drive will be mounted and will appear on your desktop.  The user should ownership of the files on the drive now.

edit: you will have to unmount from the terminal using "pumount".  See the man page for pmount for more details.

---

### Post by rocketman768 on 2008-01-12
Rocket, all good advice, but I don't think you are answering his/her question. I am pretty sure it has to do with hal. Look at this [http://wiki.archlinux.org/index.php/HAL]("http://wiki.archlinux.org/index.php/HAL") and go down to the section that says "Automount only removable media".

---

### Post by Rocket2DMn on 2008-01-12
> **rocketman768 said:**
> Rocket, all good advice, but I don't think you are answering his/her question. I am pretty sure it has to do with hal. Look at this [http://wiki.archlinux.org/index.php/HAL]("http://wiki.archlinux.org/index.php/HAL") and go down to the section that says "Automount only removable media".

There's some good information in that page, but that automount only removable media part just says that it does automount, not really how (granted it tells us HAL does it).  The reason I told him to look at dmesg is because here you can see a bunch of output about recognizing and then mounting a USB drive that is plugged in.  Here is what I see when I plug in my external USB disk
```
[320428.320000] usb 4-1: new high speed USB device using ehci_hcd and address 15
[320428.452000] usb 4-1: configuration #1 chosen from 1 choice
[320428.484000] scsi15 : SCSI emulation for USB Mass Storage devices
[320428.484000] usb-storage: device found at 15
[320428.484000] usb-storage: waiting for device to settle before scanning
[320433.484000] usb-storage: device scan complete
[320433.484000] scsi 15:0:0:0: Direct-Access     UDISK    PDU01_1G  61G2.0 0.00 PQ: 0 ANSI: 2
[320433.488000] sd 15:0:0:0: [sdb] 1967616 512-byte hardware sectors (1007 MB)
[320433.488000] sd 15:0:0:0: [sdb] Write Protect is off
[320433.488000] sd 15:0:0:0: [sdb] Mode Sense: 00 00 00 00
[320433.488000] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[320433.492000] sd 15:0:0:0: [sdb] 1967616 512-byte hardware sectors (1007 MB)
[320433.492000] sd 15:0:0:0: [sdb] Write Protect is off
[320433.492000] sd 15:0:0:0: [sdb] Mode Sense: 00 00 00 00
[320433.492000] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[320433.492000]  sdb: sdb1
[320433.540000] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[320433.540000] sd 15:0:0:0: Attached scsi generic sg2 type 0
[320545.328000] UDF-fs: No VRS found
[320545.336000] UDF-fs: No VRS found
[320545.456000] Unable to identify CD-ROM format.
[320545.540000] Unable to identify CD-ROM format.
[320545.544000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[320962.600000] usb 4-1: USB disconnect, address 15
[321989.472000] usb 4-1: new high speed USB device using ehci_hcd and address 16
[321989.656000] usb 4-1: configuration #1 chosen from 1 choice
[321989.660000] scsi16 : SCSI emulation for USB Mass Storage devices
[321989.660000] usb-storage: device found at 16
[321989.660000] usb-storage: waiting for device to settle before scanning
[321994.660000] usb-storage: device scan complete
[321994.660000] scsi 16:0:0:0: Direct-Access     ST330083 1A               3.01 PQ: 0 ANSI: 0
[321994.664000] sd 16:0:0:0: [sdb] 586072367 512-byte hardware sectors (300069 MB)
[321994.664000] sd 16:0:0:0: [sdb] Write Protect is off
[321994.664000] sd 16:0:0:0: [sdb] Mode Sense: 03 00 00 00
[321994.664000] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[321994.664000] sd 16:0:0:0: [sdb] 586072367 512-byte hardware sectors (300069 MB)
[321994.668000] sd 16:0:0:0: [sdb] Write Protect is off
[321994.668000] sd 16:0:0:0: [sdb] Mode Sense: 03 00 00 00
[321994.668000] sd 16:0:0:0: [sdb] Assuming drive cache: write through
[321994.668000]  sdb: sdb1
[321994.680000] sd 16:0:0:0: [sdb] Attached SCSI disk
[321994.680000] sd 16:0:0:0: Attached scsi generic sg2 type 0

```
Then on unmount and power off:
```
[322139.860000] usb 4-1: USB disconnect, address 16

```

If the OP would like, I can explain in a little more detail what is happening, though it's pretty self-explanatory though seemingly cryptic.

All this is what is actually happening in the system, hence the "how".

---

### Post by chandru.in on 2008-01-20
Sorry for such a delayed reply.

I get the flow in the dmesg output.  But I think dmesg is just about ataching and detaching devices.  Like I plug in the USB key, the kernel sees it and makes a file in /dev/.

But what I ant is something like this.  Say I'm using Ubuntu in terminal mode as a normal user.  Now I plugin a USB key.  How do I mount and use it?  I do not have sudo permissions.

---

### Post by Rocket2DMn on 2008-01-20
Without sudo permissions you will have to use a program called pmount, it is available in the repositories as is used the same way as mount (which requires root privileges).  So say your USB key is formatted with FAT32 or FAT16 and Ubuntu puts the device at /dev/sdb1.
```
mkdir /media/mydisk
pmount -t vfat /dev/sdb1 /media/mydisk
```

However, if you can't install due to lack of sudo privileges...
You can allow yourself access to sudo by doing the following.   Reboot the computer into recovery mode and you will be given a terminal with root login, no password required.  Type out
```
adduser username admin
``` where username is your normal login.  Alternatively from that terminal, edit the group file directly with
```
nano /etc/group
```
and add your name to the "admin" group, like
```
admin:x:117:username,someotheruser,etc,etc
```
the number may be different for you, and you probably only need 1 user to be listed (yourself!).

I suggest the first method with "adduser", but either will work.

---

### Post by chandru.in on 2008-01-22
Thanks for that info.  I'll use pmount.

---

