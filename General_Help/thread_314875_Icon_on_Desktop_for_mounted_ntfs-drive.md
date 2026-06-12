---
title: "Icon on Desktop for mounted ntfs-drive"
date: 2006-12-08
forum: General Help
---

### Post by gaspedalo on 2006-12-08
Hi! I mount my ntfs partition into /media/Windisc, everything is working out, but I miss the Icon on the desktop and inside the Computer:/// Environment. CDRoms create Icons on desktop, I switched on to show them in the configurationmanager/apps/nautilus. But no icon for the NTFS Drive. Any hint?

I use EdgyEfter on a HP Notebook. I mount with a sudo mount ... shell script.

Daniel

---

### Post by strabes on 2006-12-08
I have the same problem with my rockbox-using vfat iPod. here's the output of mount:

> /dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
/dev/sda4 on /home type ext3 (rw)
/dev/sda2 on /media/data type ext3 (rw)
/dev/sda3 on /media/sda3 type ext3 (rw)
/dev/sda4 on /media/sda4 type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb2 on /media/ipod type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

I assume that it has something to do with one of the flags on the last line. Does anyone know which one I should change/add in order to make my iPod appear on my desktop? How would I edit these? Thanks for any help.

---

### Post by gaspedalo on 2006-12-09
Actually I've know idea about what is happening here (or better, what is not happening) but I assume that there ain#t no problem with mount but ith some gnome preferences. We can mount the discs, we can use it, just gnome is ignoring it, so it doesn't activate those icons.

---

### Post by strabes on 2006-12-09
yeah it's just wierd because my mounted ext3 shared partition is showing up on the desktop...... :(

---

### Post by gaspedalo on 2006-12-18
BTW, mounting with fstab at startup makes the Icon appear on the DT.

---

### Post by strabes on 2006-12-18
so should I add a line in /etc/fstab for my ipod? How do I find out its /dev location?

---

### Post by Buck2348 on 2006-12-26
> **strabes said:**
> so should I add a line in /etc/fstab for my ipod? How do I find out it's /dev location?My usb memory card shows up on the list when I type a "mount" command (with no arguments).

Buck

---

