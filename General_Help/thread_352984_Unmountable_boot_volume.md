---
title: "Unmountable_boot_volume"
date: 2007-02-04
forum: General Help
---

### Post by jesus5511 on 2007-02-04
Okay, I've now gone through a lot of trial and error (including reinstalling windows about 3 times within 2 or 3 hours) and I just cannot get Windows XP Pro to boot, it now brings up an "Unmountable_boot_volume" error that I can't seem to get rid of. I've already tried the chkdsk /p and /r parameters but they both bring up a "unresovolable issue error" and fixboot can't find the disk. I tried editing my boot.ini file:

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect


so that the rdisk was one, but Ubuntu won't let me save because the drive is read only. 

Is their anyway to fix this?

---

