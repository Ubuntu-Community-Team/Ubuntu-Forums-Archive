---
title: "Problems mounting a FreeBSD UFS partitioned hard drive"
date: 2013-10-11
forum: General Help
---

### Post by wrkr1 on 2013-10-11
I followed these instructions:

[http://askubuntu.com/questions/85154/mount-ufs-filesystem](http://askubuntu.com/questions/85154/mount-ufs-filesystem)

But the hard drive is still inaccessible even when it is mounted in read mode.

I'm hoping to copy more data to the hard drive.

---

### Post by L486XGW on 2013-10-11
So what are you having problems with? Post errors you are getting or why exactly it is not working.

---

### Post by wrkr1 on 2013-10-18
I'm sorry I did not include details.

There is a 2TB UFS-formated hard drive in a modular non-RAID external USB enclosure.

I get this popup error when I plug the drive in and Ubuntu tries to automount:


```
** Unable to access &#8220;2.0 TB Volume&#8221;**

Error mounting /dev/sdd1 at /media/a4090/disk: Command-line `mount -t "ufs" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdd1" "/media/a4090/disk"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by wrkr1 on 2013-10-18
At this point I enter commands to mount UFS manually (using this as a reference [http://askubuntu.com/questions/85154/mount-ufs-filesystem](http://askubuntu.com/questions/85154/mount-ufs-filesystem) )
This is the output from the CLI:

[HTML]a4090@x785:~$ sudo modprobe ufs
[sudo] password for aaa: 
a4090@x785:~$ mkdir ~/ufs_mount
a4090@x785:~$ sudo mount -r -t ufs -o ufstype=ufs2 /dev/sdd1 /home/aaa/ufs_mount
a4090@x785:~$[/HTML]

After these manipulations I go to the file manager that now sees the volume in question as mounted, but when I click on it I get the following popup error:

```
** This location could not be displayed.**

You do not have the permissions necessary to view the contents of &#8220;ufs_mount&#8221;. 
```




In the file manager, when I navigate to /home/aaa/ufs_mount (with a mouse, of course) I am able to open the folder with no errors, but there are no visible files within it.

---

