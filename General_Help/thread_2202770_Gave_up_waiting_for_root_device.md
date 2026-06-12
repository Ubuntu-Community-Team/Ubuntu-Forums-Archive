---
title: "Gave up waiting for root device"
date: 2014-01-30
forum: General Help
---

### Post by thault on 2014-01-30
I've not had any problems till I uninstalled the Ubuntu desktop GUI on my server. Now when I start the server it dumps me into an initramfs prompt telling me that my root partition doesn't exist. More specifically /dev/mapper/TServer--vg-root. This also happens when I run Recovery mode on the computer. But I can see the root, and all other partitions, when I use the CD rescue mode, and when I boot into the root from the cd /dev/mapper/TServer--vg-root is there. I do use LVM.

---

### Post by jeanjd63 on 2014-01-31
Hello

In liveCD could you give the return of :
**sudo lvdisplay**

---

### Post by thault on 2014-01-31
It returned command not found. I boot into my TServer--vg/root. Correct?

---

### Post by jeanjd63 on 2014-02-01
And

**sudo  fdisk  -l**

---

### Post by thault on 2014-02-02
After typing sudo fdisk -l:

It went through and said all my partitions doesnt contain a valid partition table.

---

### Post by thault on 2014-02-02
here's a slew of data from Boot-Repair:
[http://paste.ubuntu.com/6865397/](http://paste.ubuntu.com/6865397/)

---

