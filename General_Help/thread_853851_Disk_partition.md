---
title: "Disk partition"
date: 2008-07-08
forum: General Help
---

### Post by stranger4u on 2008-07-08
Hi all, I am trying to create a partition on the existing drive but I always get this message:

Could not unmount /dev/sda1

The partition could not be unmounted from the following mountpoints:

/

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

I absolutely new to ubuntu. Can any of you help me out with this.

Thanks

---

### Post by Car60n on 2008-07-08
try using gparted.

---

### Post by stranger4u on 2008-07-09
Yes car60n, I installed gparted and then sys->administration->partioneditor. Attached is the image of the error i get.

Thank your reply

---

### Post by Car60n on 2008-07-09
i think sda1 is your main filesystem in which ubuntu is installed..
you'll need the gparted live cd to work on it

---

### Post by plucky on 2008-07-09
> **stranger4u said:**
> Hi all, I am trying to create a partition on the existing drive but I always get this message:
Could not unmount /dev/sda1
The partition could not be unmounted from the following mountpoints: /

Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.

I absolutely new to ubuntu. Can any of you help me out with this.

Thanks


Either use the **Partition Editor** on the Live CD or download and burn a [Gparted Live Cd](http://sourceforge.net/project/showfiles.php?group_id=115843) from the link.

You cannot change mounted partitions and the **/** partition is your systems root partition,so you have to boot an offline Live CD.

Good Luck

---

### Post by stranger4u on 2008-07-09
thank you ppl. I will try what you said.

---

