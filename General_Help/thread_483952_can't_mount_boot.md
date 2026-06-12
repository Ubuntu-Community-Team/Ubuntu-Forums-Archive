---
title: "can't mount /boot"
date: 2007-06-25
forum: General Help
---

### Post by Alex99 on 2007-06-25
Hi,
I'm trying to mount my boot-partition from the live CD, but it doesn't work... I can mount the other partitions.  The harddisk was partitioned with the logical volume manager.
This is what the command lvscan yields:

```
root@ubuntu:/home/ubuntu# lvscan
Incorrect metadata area header checksum
ACTIVE '/dev/vg00/root' [3.50 GB] inherit
ACTIVE '/dev/vg00/var' [1.50 GB] inherit
ACTIVE '/dev/vg00/tmp' [1.00 GB] inherit
ACTIVE '/dev/vg00/home' [50.00 GB] inherit
ACTIVE '/dev/vg00/swap' [1.00 GB] inherit
ACTIVE '/dev/vg00/usrlocal' [1.00 GB] inherit
ACTIVE '/dev/vg00/opt' [2.00 GB] inherit
ACTIVE '/dev/vg00/usr' [3.00 GB] inherit

```

The problem "Incorrect metadata area header checksum" existed before, even when the system was working fine.

This is what I tried to do in order to mount boot:

```
root@ubuntu:/home/ubuntu# mkdir /mnt/boot
root@ubuntu:/home/ubuntu# mount /dev/vg00/boot /mnt/boot
mount: special device /dev/vg00/boot does not exist
root@ubuntu:/home/ubuntu# mount /dev/boot /mnt/boot
mount: special device /dev/boot does not exist
root@ubuntu:/home/ubuntu# mount /boot /mnt/boot
mount: /boot is not a block device
``` 

background: I did some stupid changes in /etc/X11/xorg.conf and now after booting I can't access my normal graphical user interface or the x-server.  Because of that I am not able to just copy an old xorg.conf-copy on the current file.

I'm grateful for all hints!
Alex

edit: found folder etc in /boot

---

