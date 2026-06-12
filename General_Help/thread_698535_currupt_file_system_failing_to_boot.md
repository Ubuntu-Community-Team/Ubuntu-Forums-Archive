---
title: "currupt file system failing to boot"
date: 2008-02-16
forum: General Help
---

### Post by onesojourner on 2008-02-16
My ubuntu partition is broke. I get to the point in boot up where the ubuntu logo comes up with the loading bar under it. I get about 1/10 of the way through on the bar and it freezes. If I try to access the partition from windows now, it says it is not formatted.

---

### Post by zanak on 2008-02-16
please post you /boot/grub/menu.lst

---

### Post by onesojourner on 2008-02-16
how can I post that?

---

### Post by pointone on 2008-02-16
When booting, press Esc when prompted to access the full GRUB menu (if it doesn't open by default), then select the line for Ubuntu and press "e". This should bring up a second menu where you can select the "kernel" line and remove "quiet" and "splash" from the list of options. This will cause the boot process to be more verbose and may give you a clue as to what's happening. Post the last few lines that are displayed before it freezes (if it does indeed freeze).

Furthermore, try booting into recovery mode and see if that succeeds.

---

### Post by zanak on 2008-02-16
just copu/past it on the forum 
sudo gedit /boot/grub/menu.lst 

copy/past

---

### Post by louieb on 2008-02-16
> **onesojourner said:**
> If I try to access the partition from windows now, it says it is not formatted.
Windows needs help to read a Linux partition. It will always say a Linux partition is not formatted.  Here's a couple of helpers. 
[Explore2fs ext3 viewer - read only]("http://www.chrysocome.net/explore2fs")
[Ext2 IFS Win w/write support]("http://www.fs-driver.org/index.html")

The fact that you get the GRUB menu is good. That means GRUB can read your Linux partition. 

After choosing Ubuntu from GRUB and the loading has stalled press Ctrl+Alt+F1. That will display  the startup messages.

---

