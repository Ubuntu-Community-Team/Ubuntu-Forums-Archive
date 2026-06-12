---
title: "windows partitions"
date: 2007-11-02
forum: General Help
---

### Post by marc7777 on 2007-11-02
hello,
 after upgrading to 7.10 I cant see my windows anymore.

This is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdc2 / ext3 defaults,errors=remount-ro 0 1
/dev/hdc6 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 ro,user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

/dev/hda5 /home/marc/Desktop/win_d vfat iocharset=utf8,umask=000 0 0
/dev/hda1 /home/marc/Desktop/win_c ntfs iocharset=utf8,umask=000 0 0
/dev/hda6 /home/marc/Desktop/win_e vfat iocharset=utf8,umask=000 0 0

When I do sudo mount -a I get this:

mount: /dev/hda5 is al aangekoppeld of /home/marc/Desktop/win_d is bezig
mount: /dev/hda1 is al aangekoppeld of /home/marc/Desktop/win_c is bezig
mount: /dev/hda6 is al aangekoppeld of /home/marc/Desktop/win_e is bezig

al aangekoppeld means ;already attached
is bezig means : is busy

HELP

---

### Post by Pumalite on 2007-11-02
Sometimes this seems to happen because Windows has not been closed properly.

---

### Post by marc7777 on 2007-11-03
The strange thing is that there is no problem when I boot with an old kernel of Ubuntu

---

### Post by marc7777 on 2007-11-07
HELP anyone an idea?

---

