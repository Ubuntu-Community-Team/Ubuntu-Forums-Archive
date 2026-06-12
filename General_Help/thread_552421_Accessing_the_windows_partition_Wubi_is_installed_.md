---
title: "Accessing the windows partition Wubi is installed on"
date: 2007-09-16
forum: General Help
---

### Post by jimbouzouf on 2007-09-16
Hello,

Is there any way to mount the windows partition Wubi is installed on using UTF-8. My problem is that all my files named with a character such as "é" are invisible under Ubuntu.

According to nfs3-g Q&A this is due to a boot order issue where the partition is mount before the language specific configuration. Since virtual disks are on that partition I understand quite well why it is mounted first, but is there any way to mount a partition twice?

I tried some tweaking of my fstab file.

/media/host/wubi/disks/system.virtual.disk / ext3 loop,sync 0 1
/media/host/wubi/disks/home.virtual.disk /home ext3 loop,sync 0 2
/media/host/wubi/disks/swap.virtual.disk none swap sw 0 0
/dev/hda2 /media/Edisk ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
/dev/hda1 /media/windows ntfs-3g defaults,locale=fr_FR.UTF-8 0 0

For hda1 (windows partition) everything work fine, but on hda2 (Wubi partition) not that well...

/media/Edisk is an empty file, my partition is mounted with another name (windows name) in /media/host but it doesn't use the utf-8 language configuration therefore a lot of my files are invisible to me...

If anyone got a solution for me I thank him in advance.

---

### Post by ago on 2007-09-17
> **jimbouzouf said:**
> Hello,

Is there any way to mount the windows partition Wubi is installed on using UTF-8. My problem is that all my files named with a character such as "é" are invisible under Ubuntu.

According to nfs3-g Q&A this is due to a boot order issue where the partition is mount before the language specific configuration. Since virtual disks are on that partition I understand quite well why it is mounted first, but is there any way to mount a partition twice?

I tried some tweaking of my fstab file.

/media/host/wubi/disks/system.virtual.disk / ext3 loop,sync 0 1
/media/host/wubi/disks/home.virtual.disk /home ext3 loop,sync 0 2
/media/host/wubi/disks/swap.virtual.disk none swap sw 0 0
/dev/hda2 /media/Edisk ntfs-3g defaults,locale=fr_FR.UTF-8 0 0
/dev/hda1 /media/windows ntfs-3g defaults,locale=fr_FR.UTF-8 0 0

For hda1 (windows partition) everything work fine, but on hda2 (Wubi partition) not that well...

/media/Edisk is an empty file, my partition is mounted with another name (windows name) in /media/host but it doesn't use the utf-8 language configuration therefore a lot of my files are invisible to me...

If anyone got a solution for me I thank him in advance.

Hmm the issue is that /media/host should be remounted with the appropriate parameters, but that is not necessarily too trivial

---

### Post by Javhar on 2008-01-14
Any news on this? I have all manner of diacritics in my filenames (French, German, Dutch, Norwegian...) so this is crucial to me.

---

### Post by ago on 2008-01-14
You will have to wait 8.04 version, whose preliminary alpha should be out soon.

---

### Post by gsrkashyap on 2008-01-31
can we update to 8.04 when it comes?

---

### Post by ago on 2008-01-31
from 7.10 yes, from 7.04 no
you can also install in parallele (sort of)

---

### Post by stefanpv on 2008-04-30
Hello,
installed 8.04 and have still the same problem (with german ö,ä....).
Tried to mount sde1 with nls=utf8, but no effect. Is there any workaround? 
Thanks!

---

### Post by ago on 2008-04-30
I provided a few suggestions in:

[https://bugs.launchpad.net/wubi/+bug/136682](https://bugs.launchpad.net/wubi/+bug/136682)

It would also be interesting to try mounting the same partition off a Live CD using the locale mount option

---

