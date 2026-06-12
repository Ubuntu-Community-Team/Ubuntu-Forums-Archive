---
title: "Can't mount hda (mdadm not seeing it)"
date: 2006-11-13
forum: General Help
---

### Post by tengil on 2006-11-13
Anyone know how to fix this:
  mdadm: /dev/md0 has been started with 1 drive (out of 2)

It's not seeing my hda after install of dapper server (installer found it so did a previous 5.10 desktop).

Had to install to hdd, but still can't mount hda.

Here's what I got after installing to hda:

```

Uncompressing Linux... Ok, booting the kernel.
mdadm: /dev/md0 has been started with 1 drive (out of 2).
mdadm: /dev/md1 has been started with 1 drive (out of 2).
mount: Mounting /dev/hda1 on /root failed: Device or resource busy
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

BusyBox v1.01 ...

```

After installing to hdd I get this during boot:

```
mdadm: /dev/md0 has been started with 1 drive (out of 2)
```

and then I can't mount hda:

```

$ sudo mount /dev/hda1 t
mount: /dev/hda1 already mounted or t busy

$ mount
/dev/hdd1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)

```

---

