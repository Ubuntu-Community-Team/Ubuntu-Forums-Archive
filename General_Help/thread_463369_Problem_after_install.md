---
title: "Problem after install"
date: 2007-06-03
forum: General Help
---

### Post by wkw2 on 2007-06-03
I just installed Ubuntu 6.10 Edgy Eff - install went fine.  This will replace the older version I am running now.

On the Gnome desktop, I pulled down the System menu and go to Administration because I want to add the other disks that I have on the machine but there is no Disks icon there.

Haven't really looked any further since I need to get this problem taken care of before I can go further.

Any help would be greatly appreciated.

Ken

---

### Post by merlinus on 2007-06-03
In a terminal:

sudo fdisk -l

(l is a lowercase L)

Post the results.

-merlin

---

### Post by wkw2 on 2007-06-04
When I run sudo fdisk -l all it shows is the boot disk hda

The devices tool shows other disks but fdisk does not.

Ken

---

### Post by init7 on 2007-06-05
Does BIOS detected the new harddrive?

---

### Post by wkw2 on 2007-06-05
The hardware is not new.  I have installed one new disk drive (the boot drive) which is detected by BIOS.

There is another drive on the machine with Linux ext 3 parts on it - this is also seen by the BIOS and when I use the Device Manager on the System pull down menu.  (System -> Administration -> Device Manager)

Still no Disks icon on the System -> Administration pull down.

Ken

---

