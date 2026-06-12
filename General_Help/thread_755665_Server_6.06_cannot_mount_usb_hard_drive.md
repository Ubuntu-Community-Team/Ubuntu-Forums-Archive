---
title: "Server 6.06 cannot mount usb hard drive"
date: 2008-04-15
forum: General Help
---

### Post by phillips321 on 2008-04-15
Hi guys,

external usb hard drive is formatted to ext3.

if i boot with the drive plugged in then i cannot access the drive until i get someone locally to unplug/replug it, here's the output of a few commands to help get the ball rolling

```
phillips321@LinuxHTTP:~$ sudo -s
root@LinuxHTTP:~# fdisk -l

Disk /dev/hda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         122      979933+  82  Linux swap / Solaris
/dev/hda2   *         123        2431    18547042+  83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux
root@LinuxHTTP:~# mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
root@LinuxHTTP:~# mount /dev/sda1 /media/data
mount: /dev/sda1 already mounted or /media/data busy
root@LinuxHTTP:~#
```

does anyone here know how to get around this?

i don't have anything it fstab that references the drive:
```
root@LinuxHTTP:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

root@LinuxHTTP:~#
```

---

### Post by phillips321 on 2008-04-15
please please please help guys, even just by pointing me in the right direction.

I really cant understand why i cannot mount the drive after booting with it connected.

Really defeats the object of having an external usb drive connected to a server :(

---

### Post by phillips321 on 2008-04-16
Come on guys, i can't be the only mug who's experiencing this???

---

### Post by dsnyders on 2008-04-16
Mounting USB devices is not as simple as mounting IDE drives.  There is a service which I think is called udev that monitors the USB ports for device plug-ins and plug-outs.  When udev detects that the USB drive gets plugged in, it issues the appropriate commands to mount the drive, and when it is removed, udev unmounts it. It seems that on your system udev is not detecting the drive if it is already present on startup.

A couple of things you might try:
1 Compare your fstab with the drive unmounted vs when the drive is mounted.  You should see an extra line. You could try altering the automount flag on that line.
2 Check the /etc/udev-rules (or whatever) files to see if there is a check-for-device-on-boot type of parameter that needs altering.

I hope this helps.  (I'd start by looking at the second thing, myself).

---

### Post by phillips321 on 2008-04-16
When i plug the drive in it doesn't automatically mount, i have to manually issue the "mount /dev/sda1 /media/data" command.

I will investigate further with udev though, thx

---

