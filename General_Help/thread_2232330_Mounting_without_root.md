---
title: "Mounting without root"
date: 2014-07-01
forum: General Help
---

### Post by CaptainMark on 2014-07-01
I was under the impression that so long as a device has an entry in fstab and the mount point is owned by the user, then the user can mount the device without root, but I'm having problems, I keep getting a message telling me the device is not found in /etc/fstab, but it is. See the code below, what to do?
```

[10:20:08] mark@server ~ $ cat /etc/fstab |grep media
/dev/disk/by-id/usb-Generic-_SD_MMC_20090815198100000-0\:0-part1    /media/usb-Generic-_SD_MMC_20090815198100000-0\:0-part1    vfat    defaults,user,noauto    0    0
[10:20:09] mark@server ~ $ ls -lah /media/
total 12K
drwxr-xr-x  3 root root 4.0K Jul  1 09:45 .
drwxr-xr-x 23 root root 4.0K May 18 15:44 ..
drwxr-xr-x  2 mark mark 4.0K Jul  1 09:45 usb-Generic-_SD_MMC_20090815198100000-0:0-part1
[10:20:22] mark@server ~ $ mount /dev/disk/by-id/usb-Generic-_SD_MMC_20090815198100000-0\:0-part1
mount: can't find /dev/disk/by-id/usb-Generic-_SD_MMC_20090815198100000-0:0-part1 in /etc/fstab or /etc/mtab

```What am I doing wrong?

---

### Post by vanadium on 2014-07-01
Yuo may need to provide an escape for the \ as well, i.e. ...\\\: rather than \:

---

### Post by TheFu on 2014-07-01
1) try using quotes around any file/directory that has spaces in the name. I didn't look close enough to tell if that is happening. Perhaps not.

mount is an extremely powerful command. It is only in recent years that someone decided a non-root user should have access to it - which I disagree about.  I think mounting only works for non-root when the mount point is under /media/ .  With mount, users can alter permissions and give out root-level controls.

However, there is an alternative. **autofs**.  It will mount partitions on-demand. Basically, until a user cds or otherwise accesses the storage, it isn't mounted. If the storage isn't connected, it will try to mount it, but eventually timeout ... this may or may not lock up the system during that period, so it is best to use soft mounts on some-times-there storage.  However, soft mounts have issues that should be understood. RTFM.  Hard mount are safer for our data.

The autofs stuff is based on the old automounter or AMD from the 1990s. I use it all over the place here - even from laptops. It is important to never attempt accessing storage that isn't currently available. Other than that, it is extremely convenient.

---

### Post by sisco311 on 2014-07-01
You don't have to escape the : (colon) in the file name. 

```
#/etc/fstab
#...

/dev/disk/by-id/usb-Generic-_SD_MMC_20090815198100000-0:0-part1    /media/usb-Generic-_SD_MMC_20090815198100000-0:0-part1    vfat    defaults,user,noauto    0    0

#...
```
By default, users are allowed to mount external drives without a password. You can use udisks to do it without the need for an fstab entry: [uhelp]community/AutomaticallyMountPartitions[/uhelp]

---

