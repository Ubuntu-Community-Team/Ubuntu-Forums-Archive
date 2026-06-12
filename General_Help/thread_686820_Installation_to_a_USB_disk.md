---
title: "Installation to a USB disk"
date: 2008-02-03
forum: General Help
---

### Post by obarriel on 2008-02-03
I am trying to use Wubi in a USB disk (unit d:). It is a Eeepc so I have no other option since the internal hdd is very small.

When windows reboots and the Ubuntu installation should start I get the busybox shell. The only log I have found is casper.log that finishes saying:

"Unable to find a medium containing a live file system"

What can I do?

---

### Post by ago on 2008-02-04
Probably the USB is mounted too slowly and by the time we look for the wubi installation files it is not yet up. Have a look in cat /proc/partitions if the partition is available and if the files are there.

---

### Post by obarriel on 2008-02-04
Thank you for your answer .Apparently it is well mounted,

It says:

#blocks      name
3907512    sda
3903762    sda1
15694336  sdb
15687441  sdb1

Internal memory is only 4gb and I am using a 16gb USB

---

### Post by ago on 2008-02-04
That means that the usb is visible to the OS. The issue is that it takes some time for it to become visible (depending on hardware), and if we happen to look for a file or drive before then, we wil fail to see it.

If you boot in verbose mode and send me casper.log  I will be able to confim that, see the last posts on the 8.04 thread on how to do that (basically mount manually any windows partition and copy the log files there).

---

### Post by obarriel on 2008-02-04
When I try to mount the hdd in /tmpmnt to copy the logfile there it says:

mount: cannot read /etc/fstab: No such file or directory :confused:

---

### Post by ago on 2008-02-04
mount -t ntfs /dev/sda1 /tmpmount

---

### Post by obarriel on 2008-02-04
Here you have

Thank you very much :)

---

### Post by ago on 2008-02-04
Yes that looks like a device delay issue, will fix that in the future. 

What wubi/iso version are you using by the way?

---

### Post by obarriel on 2008-02-04
Wubi 7.10 Alpha 386 and Ubuntu 7.10 Desktop i386

Hope you can fix it for future versions

Thank you!

---

### Post by ago on 2008-02-04
Fix committed [https://bugs.launchpad.net/wubi/+bug/188952](https://bugs.launchpad.net/wubi/+bug/188952)

---

