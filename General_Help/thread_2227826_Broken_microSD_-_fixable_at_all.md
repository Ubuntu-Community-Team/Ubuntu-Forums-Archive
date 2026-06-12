---
title: "Broken microSD - fixable at all?"
date: 2014-06-04
forum: General Help
---

### Post by PaganRuler on 2014-06-04
Hi,

Below is the error message I get trying to mount this 64GB microSD card. In gparted there is a 16MB sector and a 59GB exFat sector that I can't delete or do anything to.

I have tried Disk Utility and gparted to format but it kicks up an error, or looks like its done something and then brings the partitions back up looking the same.

As its a 64GB card I'd like to try my best to save it as they aren't just a few quid.

Thanks


Error mounting /dev/mmcblk0p1 at /media/it/DD98-1646: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/mmcblk0p1" "/media/it/DD98-1646"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

---

### Post by sudodus on 2014-06-04
Welcome to the Ubuntu Forums :-)

Flash cards can have a hardware switch to make them read-only. Check if there is one (and what happens if there is and you switch it to the other position).

Newer Ubuntu systems can manage the exfat file system. In older Ubuntu system you might need a special driver to manage exfat. But anyway, if the flash card is good, it should be possible to edit partitions and create file systems, 'format' it.

---

### Post by tgalati4 on 2014-06-04
If you don't need to save or recover the data, then I would find a camera or phone and reformat it from that device.  

As *sudodus* suggests, install the exfat utilities and try to format it in Ubuntu.

> tgalati4@Mint14-Extensa ~ $ apropos exfat
exfat: nothing appropriate.
tgalati4@Mint14-Extensa ~ $ apt-cache search exfat
exfat-fuse - read and write exFAT driver for FUSE
exfat-utils - utilities to create, check, label and dump exFAT filesystem


---

