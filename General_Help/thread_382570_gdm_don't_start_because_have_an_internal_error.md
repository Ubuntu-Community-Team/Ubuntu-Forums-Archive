---
title: "gdm don't start because have an internal error"
date: 2007-03-12
forum: General Help
---

### Post by tyrchyus on 2007-03-12
hi
I'm an italian user. I know a little english.. I hope you understand me...

A have an internal error of gdm...
this is the error:

```
Could not start the X server due to some internal error. Please contact your system administrator or check our syslog to diagnose. In the meantime this display will be disabled. Please restart GDm when the problem is corrected.
```

/etc/fstab

```

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/hdc /cdrom iso9660 ro 0 0
/dev/loop0 /rofs squashfs ro 0 0
tmpfs /cow tmpfs rw 0 0
unionfs / unionfs rw,dirs=/cow=rw:/rofs=ro,debug=0,delete=whiteout,copyup=preserve 0 0
unionfs /dev/.static/dev unionfs rw,dirs=/cow=rw:/rofs=ro,debug=0,delete=whiteout,copyup=preserve 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hda1 /mnt/work ext3 rw,data=ordered 0 0
udev /mnt/work/dev tmpfs rw 0 0
none /mnt/work/proc proc rw,nosuid,nodev,noexec 0 0
udev /mnt/work/dev tmpfs rw 0 0
none /mnt/work/proc proc rw,nosuid,nodev,noexec 0 0
udev /mnt/work/dev tmpfs rw 0 0
none /mnt/work/proc proc rw,nosuid,nodev,noexec 0 0

```

/etc/mtab

```

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/hdc /cdrom iso9660 ro 0 0
/dev/loop0 /rofs squashfs ro 0 0
tmpfs /cow tmpfs rw 0 0
unionfs / unionfs rw,dirs=/cow=rw:/rofs=ro,debug=0,delete=whiteout,copyup=preserve 0 0
unionfs /dev/.static/dev unionfs rw,dirs=/cow=rw:/rofs=ro,debug=0,delete=whiteout,copyup=preserve 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.17-10-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/hda1 /mnt/work ext3 rw,data=ordered 0 0
udev /mnt/work/dev tmpfs rw 0 0
none /mnt/work/proc proc rw,nosuid,nodev,noexec 0 0
udev /mnt/work/dev tmpfs rw 0 0
none /mnt/work/proc proc rw,nosuid,nodev,noexec 0 0
/dev/hda1 /boot ext3 rw 0 0

```

and now this is some error that I have..

marco@tyrchyuntu: sudo dpkg-reconfigure gdm
pssword:

chown: proprietario di '/var/lib/gdm/.cookie' è stato cambiato: file systm in sola lettura
chown: proprietario di '/var/lib/gdm/.fonts-cache-1' è stato cambiato: file system in sola lettura
chown: proprietario di '/var/lib/gdm' è stato cambiato: file system in sola lettura

marco@tyrchyuntu: sudo apt-get install gdm oppure sudo apt-get remove gdm

W: locking disabilitato per il file di lock in sola lettura in /var/lib/dpkg/lock
E: Impossibile scrivere in /var/cache/apt/
E: la lista dei pacchetti o il file di status non possono essere letti

marco@tyrchyuntu: startx

/usr/bin/startx: line 132: cannot create temp file for here document:  read-only filesystem
xauth: error in locking authority file /home/marco/.Xauthority
/usr/bin/startx: line 144: cannot create temp file for here document: read-only filesystem
xauth: error in locking authority file /home/marco/.Xauthority
/usr/bin/startx: line 144: cannot create temp file for here document: read-only filesystem

fatal server error:
could not create lock file in /tmp/.tX0-lock

giving up.
xinit: connection refused (errno 111): unable to connect to x server
xinit: no such process (errno 3): server error
xauth error in locking authority file /home/marco/.Xauthority

all problem is arrived after i have ripristinated grub with this guide:

[http://wiki.ubuntu-it.org/RipristinoGrub?highlight=%28grub%29]("http://wiki.ubuntu-it.org/RipristinoGrub?highlight=%28grub%29")
Can anybody help me??

---

### Post by tyrchyus on 2007-03-12
anyone???:popcorn:

---

### Post by tyrchyus on 2007-03-12
up!!!

---

### Post by tyrchyus on 2007-03-15
Hi

Do you know what is the command to change read-only to read-write on my filesystem?

---

### Post by Aeriuz on 2007-03-23
I've got the same kind of trouble : to change to rw instead of ro : mount -n - o remount, rw / ( maybe in sudo ) before you may try e2fsck -f -y -CO /dev/hd( your linux partition ) 

After that try dpkg-reconfigure xserver-xorg and dpkg-reconfigure gdm. If you're lucky everything may work fine :) ( personnaly i'm stuck with gdm). You can load graphical interface with startx .

---

