---
title: "External Drive not working"
date: 2006-12-23
forum: General Help
---

### Post by bslusser on 2006-12-23
I recently bought an Acomdata 320GB external usb2.0 drive. When i go to plug it in Dapper will tell me that a cd writer was found and I can't view the hard drive at all except for a portion of software that is on the hard drive to begin with. should i just return this drive?

dmesg | tail
[17466340.724000] sr 2:0:0:0: Attached scsi generic sg0 type 5
[17466340.724000]   Vendor: DMI       Model: USB2.0 Storage    Rev: 1.15
[17466340.724000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17466340.728000] sd 2:0:0:1: Attached scsi disk sda
[17466340.728000] sd 2:0:0:1: Attached scsi generic sg1 type 0
[17466340.728000] usb-storage: device scan complete
[17466350.228000] UDF-fs: No VRS found
[17466350.252000] UDF-fs: No VRS found
[17466350.276000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17466350.276000] ISO 9660 Extensions: RRIP_1991A

---

### Post by bslusser on 2006-12-23
I should add this too
/etc/mtab

/dev/hde5 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
/dev/hdg1 /home ext3 rw 0 0
/dev/scd0 /media/scd0 iso9660 ro,noexec,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8 0 0

the /media/scd0 is what my HD is registering as. any thoughts?

---

### Post by crispy_420 on 2006-12-24
If is formatted to NTFS you may have issues with read and write.

---

### Post by logos34 on 2006-12-24
does your BIOS also recognize it as a dvd/cdrom?

---

### Post by bslusser on 2006-12-24
The user manual told me that it is formatted in FAT32 so it should be good there. I am not sure if my bios detects it as anything. but when i plug it in it comes up as a cd writer. this external Hd is compatible with osx and windows so i just thought that it would be compatible with linux as well. is there a possibility that this is a windows/osx only thing ?

---

### Post by logos34 on 2006-12-24
Your USB hard drive should show up as /dev/sda1...it's probably just a matter of creating a directory like '/media/sda1', then editing /etc/fstab so that it reads something lke

/dev/sda1 /media/sda1 vfat iocharset=utf8,umask=000,uid=1000,gid=1000,auto,rw ,nouser 0 0

then it should mount correctly.

DON"T do this yet, though--try to get the attention of one of the moderators like taurus to walk you through it.

---

### Post by bslusser on 2006-12-24
I only have a /dev/sda  not /dev/sda1

---

### Post by zombie_killer on 2006-12-24
If there is a partition on the drive, it should come up as sda1.  The context of sdAB is A=drive letter and B=partition.  You can't just mount the drive, you actually have to mount the partition.

Run gparted and see what that tells you.  If there's a partition, gparted will tell you about it.  If not, use gparted to make one.

And, no, there shouldn't be an issue of it being Windows/OSX compatible.  It should work fine in Ubuntu.

---

### Post by bslusser on 2006-12-24
gparted only shows my 2 internal hard drives hde and hdg

I wonder if this drive can only be used with proprietary software for osx or windows only?
[http://www.acomdata.com/hdp/harddrives-HDxxxUHE5-72.html](http://www.acomdata.com/hdp/harddrives-HDxxxUHE5-72.html)

---

### Post by zombie_killer on 2006-12-24
Did you try logos34's suggestion for your fstab entry?  I'd try replacing your current entry with that one, then rebooting.

---

### Post by bslusser on 2006-12-24
it didnt work. I am wondering if this drive can only be used with the manufacturers software since when i plug it in I can view the windows/osx software install partition that supposedly can't be deleted.  I might just have to take it back

---

### Post by zombie_killer on 2006-12-24
There's got to be a way of wiping the sucker clean.  It's just a harddrive--you can't really keep someone from deleting information off of it, especially if they just format it.  So that's what I'd try to do.  Maybe run Windows' disk management on it, delete the partition (but don't write a new one), then use Ubuntu to repartition it.

---

