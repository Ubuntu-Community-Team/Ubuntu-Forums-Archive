---
title: "df is broken"
date: 2007-05-22
forum: General Help
---

### Post by cri on 2007-05-22
When I run `df` I get:

df: cannot read table of mounted file systems: No such file or directory

Very unfortunate. I need to fix this but have no idea how to do so. Please help.

---

### Post by Cypher on 2007-05-22
Can you do
```

ls /proc/mounts
cat /proc/mounts

```
???

---

### Post by cri on 2007-05-25
Yup, no problem.

```

[atypon@california ~]$ ls /proc/mounts
/proc/mounts@
[atypon@california ~]$ ll /proc/mounts
lrwxrwxrwx 1 root root 11 2007-05-25 10:53 /proc/mounts -> self/mounts
[atypon@california ~]$ cat /proc/mounts
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/adabf60f-f209-45b8-af07-0825e0579a13 / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/adabf60f-f209-45b8-af07-0825e0579a13 /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/mmcblk0p1 /media/sd vfat rw,nosuid,nodev,noexec,gid=29,fmask=0002,dmask=0002,codepage=cp437,iocharset=iso8859-1 0 0
//mi-tech19.office.share.org/publisher /mnt/jstor smbfs rw,nosuid,nodev,uid=0,gid=0,file_mode=0755,dir_mode=0755 0 0
/dev/sdb2 /media/ipod vfat rw,nosuid,nodev,noexec,gid=29,fmask=0002,dmask=0002,codepage=cp437,iocharset=iso8859-1 0 0
[atypon@california ~]$                                   

```

---

