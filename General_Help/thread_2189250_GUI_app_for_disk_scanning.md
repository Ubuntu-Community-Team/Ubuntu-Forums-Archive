---
title: "GUI app for disk scanning"
date: 2013-11-21
forum: General Help
---

### Post by mbnoimi on 2013-11-21
Hi guys,

Is there any GUI for hard disk scanning similar to M$ Windows?

P.S. IFW fsck is the alternative but it's CLI app.

---

### Post by jCjQszKMO5JH on 2013-11-21
Gparted has this functionality. Right click on the filesystem you want to check and click *Check*&#8203;.

---

### Post by oldfred on 2013-11-21
You can only run fsck on unmounted partitions. So if another drive it will work, but if your system drive you need to run from Live installer.

Even Windows only sets a chkdsk flag so it runs chkdsk on next reboot before file system is mounted.

---

### Post by mbnoimi on 2013-11-21
Thanks guys for help. I'm using check from KDE Partition Manager.

---

