---
title: "usb iso boot 16.04 with other partitions on same drive. file size and mount error"
date: 2017-10-17
forum: General Help
---

### Post by jd8788 on 2017-10-17
I have put the iso on the usb removable drive. I tried to use start up disk creator, it could not find are not able to put on usb, only a disk. So I did this on gparted.  It is 2TB. There is no problems to boot and most functions are fine. I am currently waiting for a new hard drive to arrive so I only boot into "try Ubuntu". I am fairly new to Linux systems ,but I have had some installed on hard drive for everyday use for a few months now. Everything has been fine until I tried this from flash drive.There are a total of 4 spaces:  iso boot for mate 16.04,  unallocated,  duke n boot, unallocated. They are in that order. At random times I receive an error message. There are three different ones. one:  gparted says volume is 2048 bytes but linux says it is 512 bytes. the options to choose to do next are as follows:  ignore, cancel.  two:                          [SIZE=3]
Error mounting /dev/sda1 at /media/ubuntu-mate/Ubuntu-MATE 16.04.3 LTS amd64: Command-line `mount -t "iso9660" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500" "/dev/sda1" "/media/ubuntu-mate/Ubuntu-MATE 16.04.3 LTS amd64"' exited with non-zero exit status 32: mount: /dev/sda1 is already mounted or /media/ubuntu-mate/Ubuntu-MATE 16.04.3 LTS amd64 busy[/SIZE]

    
                     all I can do for this dialogue is click OK.
I apologize but I have not written the third one down and can not remember it. If anyone could help with this issue I would greatly appreciate any and all help. Oh and also I have already wiped out flash drive with zeros once and im getting the same type of issue. also all 2TB before any partition was made FAT.

also is there a way to have a separate partition on this flash drive to have software files such as .tar or other repository. I would like to keep them there even after install on flash drive so that I could wipe out OS if needed but still have programs there and ready without internet for a fresh install.

---

### Post by C.S.Cameron on 2017-10-17
Try mkusb, It is a linux app that installs a Debian based iso, such as Ubuntu Mate, to flash drive.
Mkusb can create a drive with boot stuff on a FAT32 boot partition, the OS on a read only ISO9660 partition, Persistence on a ext4 partition and there is a NTFS data partition accessible to Linux or Windows. [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

Edit:
Oops, forgot my manners, welcome to the Forms.

---

### Post by jd8788 on 2017-10-19
Thank you for this info. I will give it a try as soon as I can. I will post my results. Also thanks for the welcome here.

---

