---
title: "MBR repair on a USB device involving permissions"
date: 2007-11-12
forum: General Help
---

### Post by DJ0802 on 2007-11-12
I am attempting to run Ubuntu 7.10 from USB flash drive for kicks and to try out Ubuntu.  I partitioned the drive and installed all of the necessaries only to find that the MBR is corrupted, or something of the sorts.  I have used this drive on a windows computer, but the formatting of the device with the partitioning should have taken care of any unforseen problems.  The problem comes when i attempt to install lilo i receive the following message in the terminal
ubuntu@ubuntu:~$ lilo -M /dev/sdb
Fatal: creat /boot/boot.0810: Permission denied

I have no idea how to change the permission.  I even tried taking it back to a windows computer and setting every possible share option there, but to no avail. Any wonderful divine help would be much appreciated.

---

### Post by girlfreddy on 2008-01-01
I have the same problem. Anybody?

---

### Post by az on 2008-01-01
I think that should be **sudo** lilo -M /dev/sdb...

---

### Post by nuggiehogan on 2008-02-19
It works!... Thanks AZ,

---

