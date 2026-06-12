---
title: "Low Disk Space warning"
date: 2013-04-10
forum: General Help
---

### Post by joelstitch on 2013-04-10
I am running Ubuntu 10.04 out of a 160GB external hard drive with nothing in it except a few files and the Operating System. When I made the Startup USB Disk I chose as much reserved extra space as possible so I dont know why is showing me this warnign. How do i fix it so the OS has more space dedicated to it?

```
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
aufs                  4.0G  3.8G     0 100% /
none                  871M  288K  870M   1% /dev
/dev/sda1             149G  4.7G  145G   4% /cdrom
/dev/loop0            667M  667M     0 100% /rofs
none                  876M  112K  876M   1% /dev/shm
tmpfs                 876M   12K  876M   1% /tmp
none                  876M   96K  876M   1% /var/run
none                  876M  4.0K  876M   1% /var/lock
none                  876M     0  876M   0% /lib/init/rw
```

This is what GParted says:
Partition: /dev/sda1
File System: fat32
Mount Point: /cdrom
Size: 149.05GB
Used: 4.76GB
Unused: 144.29GB
Flags: boot, lba

---

### Post by mikewhatever on 2013-04-10
Looks like you need more then 4GB for persistence. Here is the howto [http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/).

---

