---
title: "No automounting my external HD in Gutsy?"
date: 2007-10-22
forum: General Help
---

### Post by shimrodmimir on 2007-10-22
Hi everyone,

I have an external (USB Seagate FAT32) Hard drive. As it's always plugged in anyway, I would like for it to be automatically mounted from boot. Unfortunately this doesn't seem to work in Gutsy anymore (it worked fine in Feisty)

my entry in fstab reads: 
/dev/sdb1	/media/external	vfat auto,user,exec,rw,suid,dev,async,umask=000,fmask=0111,dmask=0000 0 0

but when I boot it doesn't mount

I've added a 'sudo mount /dev/sdb1' to my startup programs, but no joy

However, if I go to the terminal and just mount it there with the same command it works fine.

Any ideas?

---

### Post by keithacole on 2007-10-22
i have the same exact problem

---

### Post by simonn on 2007-10-25
Same problem here, with all four of my different external drives.

mount & pmount work fine manually.

---

### Post by jonas73 on 2007-11-01
maybe there is some sort of delay stopping them from booting at startup? you could try adding something like:
@reboot sleep 5;mount -a
to your (root) crontab

---

