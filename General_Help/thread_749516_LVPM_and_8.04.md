---
title: "LVPM and 8.04"
date: 2008-04-08
forum: General Help
---

### Post by NR1224 on 2008-04-08
I am running 8,04 on wubi, and want to transfer to a dedicated partion. Sadly, the guide is written for 7.10. Is it possible to use the 7.10 packages for Hardy? I installed the LVPM_79_all package, but when i try to run it it tells me "You are running LVPM on a host installation. You must run it on a loopmounted install" Im definantly running wubi so i have no idea what to due. Thanks

---

### Post by madjr on 2008-04-22
i need this also

---

### Post by flamelab on 2008-04-22
&#932;here is a prob for now 

[quote=WubiGuide]How do I get rid of the virtual disks and switch to real partitions, and/or get rid of Windows entirely?

Existing Wubi/Lubi 7.04/7.10 installations can be upgraded to a full, real ubuntu install with dedicated partitions using LVPM. The main site for LVPM is at [WWW] [http://lubi.sourceforge.net/](http://lubi.sourceforge.net/) and the guide and support forum is at [WWW] [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591). **[COLOR="DarkOrange"]LVPM does not yet work with Wubi 8.04. [/COLOR]**[/quote]

---

### Post by ago on 2008-04-22
If you want to expand your virtual disks, you can try to follow [https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

If you want to do a migration to dedicated partition, have a go manually:

1) format the target partition and mount it (say as /target) 
2) copy over root: 
```
rsync -avx --exclude '/proc/*' --exclude '/mnt/*' --exclude '/tmp/*'--exclude '/sys/*'  / /target/
```
3) edit /etc/fstab so that the / and /swap lines are correct for the new setup
4) remove the line with #groot from menu.lst
5) chroot and run grub-install

If you succeed feel free to edit the wubi guide

---

