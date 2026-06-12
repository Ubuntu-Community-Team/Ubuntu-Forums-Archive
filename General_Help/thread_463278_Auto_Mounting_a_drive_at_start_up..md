---
title: "Auto Mounting a drive at start up."
date: 2007-06-03
forum: General Help
---

### Post by Darkjasper on 2007-06-03
Alright I have a issue that when ever I restart my computer( not restart x only my box) that I have to remount my other internal sata hard drive using this command.

```
sudo mount -t ntfs-3g /dev/sda5 /media/sda5
```

I was just wondering if there is any way that I could put it in a config file somewhere and it would mount it at start up after a hard restart.

Thanks for any help.

---

### Post by pseudonym on 2007-06-03
[This guide]("http://www.psychocats.net/ubuntu/mountwindows") should tell you everything you need to know.

---

### Post by x1a4 on 2007-06-03
Hi,

As the super user edit your _/etc/fstab_ file and add this line to it: 

```
/dev/sda5 /media/sda5 ntfs-3g rw,suid,dev,exec,auto,nouser,async,nls=utf8,umask=0222 0 2
```

The *auto* option above tells your system to automatically mount the file system.  

To use ntfs-3g make sure you also have FUSE libraries installed.

---

### Post by strabes on 2007-06-03
Before I removed windows, I got by just fine with the following line (adjusted for your setup)
> /dev/sda5 /media/sda5 ntfs-3g defaults 0 0

---

