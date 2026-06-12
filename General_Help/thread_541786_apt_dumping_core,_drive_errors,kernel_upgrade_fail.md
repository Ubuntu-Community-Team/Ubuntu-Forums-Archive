---
title: "apt dumping core, drive errors,kernel upgrade failed"
date: 2007-09-03
forum: General Help
---

### Post by pozorvlak on 2007-09-03
Hi everyone,

I'm having some problems with my new install of Feisty on my RM laptop. The first problem was a couple of days ago when an automatic kernel upgrade failed, with error message

```
E: /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.31_i386.deb: short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.20-16-generic/kernel/drivers/net/bnx2.ko')
E: /var/cache/apt/archives/linux-libc-dev_2.6.20-16.31_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/include/linux/fd.h')
```

I've tried installing a couple of times since, with the same result (yet uname -a reports that I'm running linux 2.6.20-16...)

Since then, Gnome got very slow (occasionally freezing, especially at boot time): killing Firefox usually helped, but then that's the only memory-hungry app I usually run. While switching to a console to kill Firefox, I noticed error messages like the following:

```
[  133.432000] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  133.432000] ata1.00: (BMDMA stat 0x25)
[  133.432000] ata1.00: cmd c8/00:c0:ef:1a:c4/00:00:00:00:00/e1 tag 0 cdb 0x0 da
ta 98304 in
[  133.432000]          res 51/40:ad:02:1b:c4/00:00:00:00:00/e1 Emask 0x9 (media
 error)
[  133.504000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 7814
0160
[  133.528000] ata1.00: ata_hpa_resize 1: sectors = 78140160, hpa_sectors = 7814
0160
[  133.528000] ata1.00: configured for UDMA/33
[  133.528000] ata1: EH complete
```

These also showed up in dmesg.

Apt-get also stopped working, dumping core at the "building dependency tree" stage and complaining of a bus error. Running sudo apt-get update seems to have fixed that for now, though.

Any idea what's going on, and what I can do about it?

Thanks!

---

