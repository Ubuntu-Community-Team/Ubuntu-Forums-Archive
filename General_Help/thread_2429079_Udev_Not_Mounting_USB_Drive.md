---
title: "Udev Not Mounting USB Drive"
date: 2019-10-13
forum: General Help
---

### Post by theonlytalkinggoat on 2019-10-13
On Ubuntu 18, I have an external USB cradle with a 500gb backup drive. I have rules added in /etc/udev/rules.d that tell the drive to mount, when a new device with the correct short serial is attached. For example:
```
ACTION=="add", KERNEL=="sd?1", SUBSYSTEM=="block", ENV{ID_SERIAL_SHORT}=="DB*******17", RUN+="/bin/mount -t ext4 /dev/%k /media/backup -o rw,users,exec,suid,dev,noauto"
```

On a 16.04 system, this command works perfectly. The drive mounts to /media/backup. 

On the 18 system, nothing. The log reports the mount, but it isn't there when I run the mount command. Excerpt from syslog:
```
usb 2-1.2: SerialNumber: DB*******17
...
EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
```

```
#ls -l /media
 drwxrwxr-x  2 root adm  4096 Oct  6 08:58 backup
```

Any idea why?

---

### Post by TheFu on 2019-10-13
I haven't any clue since systemd took over the udev project and "improved" it, but you can use **autofs**, if you like.  It is a little more complex but it will mount and dismount using options we have control over.  That's a good thing for non-native file systems. It means we can specify options to help performance and prevent non-allowed filenames for those alien file systems.

Just providing an alternative.  I'd rather have udev work correctly too.

---

