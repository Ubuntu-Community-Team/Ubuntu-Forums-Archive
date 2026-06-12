---
title: "Captive NTFS is silently broken"
date: 2006-12-18
forum: General Help
---

### Post by some.hacker on 2006-12-18
I've installed captive-ntfs, and copied all the files using the download method, but I am unable to mount my firewire drive (/dev/sda1) as type captive-ntfs. When I try to, the mount command executes and exits without error, but when I check the mount point with ls it appears empty. I am able to mount this drive as type ntfs without any problems.

---

### Post by tari on 2006-12-18
I'd suggest using ntfs-3g instead of captive-ntfs, but otherwise, do you have ntfs.sys?

---

### Post by &lt;&lt;joe&gt;&gt; on 2006-12-18
lets see the command  your running

---

### Post by some.hacker on 2006-12-19
in fstab:

/dev/sda1 /mnt/ausrine captive-ntfs nodefaults,user,umask=0000 0 0

as a separate command

mount -t captive-ntfs /dev/sda1 /mnt/ausrine -o user,nodefaults,umask=0000

---

### Post by some.hacker on 2006-12-19
Ok, so it mounts correctly now, and I got it working, but whenever I reboot the computer, the following happens:

```
root@edubuntu:/home/user# mount /dev/sda1
/usr/bin/fusermount: mount failed: Invalid argument
/usr/libexec/captive-fusermount: mount failed: Invalid argument
fuse: Failed to find functional 'fusermount'. Tried locations below:
/usr/local/bin/fusermount: No such file or directory
/usr/bin/fusermount: Success
/bin/fusermount: No such file or directory
/usr/local/sbin/fusermount: No such file or directory
/usr/sbin/fusermount: No such file or directory
/sbin/fusermount: No such file or directory
/usr/libexec/captive-fusermount: Success
root@edubuntu:/home/shonen# 
Captive-WARNING **: CORBA Exception occured: id="IDL:omg.org/CORBA/COMM_FAILURE:1.0", value=0x846e28c
aborting...

```

even though...

```
root@edubuntu:/home/shonen# which fusermount 
/usr/bin/fusermount
```

chmod 711 on fusermount didnt fix anything

:-s

---

