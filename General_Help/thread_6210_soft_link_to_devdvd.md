---
title: "soft link to /dev/dvd"
date: 2004-11-26
forum: General Help
---

### Post by bob k on 2004-11-26
when I exit xfree86 or reboot I lose my soft link to /dev/dvd. I would assume that happens because the device that it is linked to (ie cdrom0) has been removed as a process of the  shutdown/restart.

My question is where an what file would I put this command at restart to create the soft link?

Sudo ln -s /media/cdrom0 /dev/dvd

I would assume the sudo is not needed while booting.

here is the code in udev.rules

# /dev/cdrom symlink
BUS="ide", KERNEL="hd[a-z]", PROGRAM="/etc/udev/cdsymlinks.sh %k", SYMLINK="%c{1} %c{2}"


TIA
Bob

---

### Post by bob k on 2004-11-28
bump

---

### Post by jdong on 2004-11-28
you could use /etc/init.d/bootmisc.sh, which is launched during bootup.

---

