---
title: "Wubi install of hardy to dedicated partition"
date: 2008-05-06
forum: General Help
---

### Post by Seks on 2008-05-06
Could someone tell me how do this manually since LVPM 8.04 isn't out yet? Do I just copy the files over and install grub or something?

_My resources:_

Windows XP with wubi installer

Ubuntu Hardy on the same partition

A Live CD with Gutsy, it won't install right but live mode is fine, so I can partition and move system files at will. 

An empty ext3 partition.

---

### Post by ago on 2008-05-07
> **Seks said:**
> Could someone tell me how do this manually since LVPM 8.04 isn't out yet? Do I just copy the files over and install grub or something?

Yes there is no black magic.

* You copy over the files to a new partition skipping /proc and /sys (cp -a)
* Then you change /etc/fstab appropriately and menu.lst (remove the #groot line, and modify #kopt) within the new installation
* Then run grub-install   
* When you reboot uninstall lupin-support

That should be it. Let me know how it goes ;)

---

### Post by Seks on 2008-05-08
> **ago said:**
> Yes there is no black magic.

* You copy over the files to a new partition skipping /proc and /sys (cp -a)
* Then you change /etc/fstab appropriately and menu.lst (remove the #groot line, and modify #kopt) within the new installation
* Then run grub-install   
* When you reboot uninstall lupin-support

That should be it. Let me know how it goes ;)

I tried copying files to the new partition with that command (also skipped "host" of course.)
I didn't understand what I should do exactly with the files, and grub-install didn't work. I changed the boot flag and rebooted and nothing loaded :(

---

### Post by darco on 2008-05-09
LVPM 8.04 should be coming out soon. The developer said some time in mid May. I am waiting for it myself. I like black magic :)

darco

---

### Post by mcastel on 2008-05-10
> **darco said:**
> LVPM 8.04 should be coming out soon. The developer said some time in mid May... 
darco

Well I'll wait too for LVPM 8.04, good that it's coming!  Meanwhile keep playing with wubi; wonderful for installing ubuntu on my old laptop without a working CDROM..;)

---

### Post by Nikas on 2008-05-20
Hm. No news?

---

### Post by ago on 2008-05-20
Yes I have added 2 scripts:

You can either move wubi to a dedicated partition: [https://wiki.ubuntu.com/WubiGuide#he...969c2d7d0ca6da](https://wiki.ubuntu.com/WubiGuide#he...969c2d7d0ca6da)

Or add a new virtual disk to increase free space: [https://wiki.ubuntu.com/WubiGuide#he...e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#he...e6bf70c6134b2b)

---

### Post by ago on 2008-05-20
Yes I have added 2 scripts:

You can either move wubi to a dedicated partition: [https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da](https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da)

Or add a new virtual disk to increase free space: [https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b)

---

### Post by Nikas on 2008-05-20
> **ago said:**
> Yes I have added 2 scripts:

You can either move wubi to a dedicated partition: [https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da](https://wiki.ubuntu.com/WubiGuide#head-410d166b798499e97402b5010a969c2d7d0ca6da)

Or add a new virtual disk to increase free space: [https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b](https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b)

Thanks!

Edit:
Changed my text. Had files on the wrong place.

---

### Post by ago on 2008-05-20
The target partition(s) must not contain any file (it is a safety check).
You can run mkfs.ext3 to vacuum them (make sure you get the right partition, because it will be wiped).

---

### Post by Nikas on 2008-05-20
> **ago said:**
> The target partition(s) must not contain any file (it is a safety check).
You can run mkfs.ext3 to vacuum them (make sure you get the right partition, because it will be wiped).

Yes. I did that. :)
Worked great! I can still dualboot and everything works as before.
Thanks again!

Edit:
"Hibernate" (suspend?) does not work. What can i do?

---

### Post by ago on 2008-05-21
Did you also allocate a swap file? Note that if you have acpi=off in menu.lst it will not work. Also for some machines hibernation/suspend does not work in ubuntu.

---

