---
title: "help with /dev assignments"
date: 2007-06-13
forum: General Help
---

### Post by grantw on 2007-06-13
I have 2 ntfs drives that I want to mount read/write in ubuntu feisty.  I understand how to use /etc/fstab and the ntfs-3g driver and have no major problems with this.  one drive is an IDE drive and the other is an external USB drive.  The problem is: it seems to be a crapshoot as to what the device gets assigned in /dev each time ubuntu boots.    for example:

sometimes one of the drives might be /dev/sdb1, sometimes /dev/sdc1, sometimes even /dev/hdb1, etc.  i haven't figured out how ubuntu decides what /dev assignment to give them.

of course this means my fstab entries sometimes don't work because i can't find a dependable way to know what path the device will be assigned in /dev.  this is very frustrating when, for example, i'm running slimserver to stream music, i reboot, and suddenly the path to my music files isn't found anymore because the drive didn't get mounted the way i expected it to (or sometimes not mounted at all).  then i have to get off my couch, go to the box, umount, and remount with ntfs-3g to the path that i wanted in the first place.  ;)

---

### Post by zer0x41 on 2007-06-13
> **grantw said:**
> I have 2 ntfs drives that I want to mount read/write in ubuntu feisty.  I understand how to use /etc/fstab and the ntfs-3g driver and have no major problems with this.  one drive is an IDE drive and the other is an external USB drive.  The problem is: it seems to be a crapshoot as to what the device gets assigned in /dev each time ubuntu boots.    for example:

sometimes one of the drives might be /dev/sdb1, sometimes /dev/sdc1, sometimes even /dev/hdb1, etc.  i haven't figured out how ubuntu decides what /dev assignment to give them.

of course this means my fstab entries sometimes don't work because i can't find a dependable way to know what path the device will be assigned in /dev.  this is very frustrating when, for example, i'm running slimserver to stream music, i reboot, and suddenly the path to my music files isn't found anymore because the drive didn't get mounted the way i expected it to (or sometimes not mounted at all).  then i have to get off my couch, go to the box, umount, and remount with ntfs-3g to the path that i wanted in the first place.  ;)

When you plug in a USB port an external hard drive or a USB stick, then Ubuntu mount them automatically in /dev/sdx  . 

When a internal hard drive is mounted it, is /dev/hdx .
 (Where "x" is whatever you want)

In case you have  2.6.20-16-generic kernel, when something is mounted, it appear to your Desktop.

Now if you mount a ntfs partition, in order to write to it, you need to install from Applications-->Add/Remove the "NTFS Configuration Tool"  and click the write mod.

---

### Post by ikonia on 2007-06-13
if your using ubuntu 6.10 or later, reference them in fstab by "block id" (the command "blkid" will give you the identifiers for each device).

This never changes. 

Udev assigns the device (/dev/sda etc etc) letters so rather than start working out why your devices are changing, just swap to blkid.

---

### Post by grantw on 2007-06-13
thanks for the help.  i ran "blkid" and see this output:

/dev/sda1: UUID="485d7c53-ac39-47f5-ab01-6c55faacf67a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="80cde18a-8588-4cee-b270-d4e5f1ee26ba" TYPE="swap" 
/dev/sdb1: TYPE="ntfs" 
/dev/sdc1: TYPE="ntfs" 

The two devices I'm speaking of here are sdb1 and sdc1 above.  Doesn't seem to show much info on them other than the filesystem type.

I thought that hd* was for internal IDE as well, but the drive above that is sdb1 right now is an internal IDE.  The other is ext USB, so it doesn't seem to necessarily follow that convention.

---

### Post by ikonia on 2007-06-13
ubuntu uses the newer version of the libata sub system, as such all disk/media devices are refered to as /dev/sd* scsi/ide/sata/usb etc etc.

---

### Post by grantw on 2007-06-13
any other ideas on how to resolve this?  blkid only shows

/dev/sdb1: TYPE="ntfs"
/dev/sdc1: TYPE="ntfs"

for my 2 ntfs drives, so there's nothing there to put in fstab.

---

