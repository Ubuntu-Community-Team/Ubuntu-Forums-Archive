---
title: "move /tmp to ram"
date: 2007-12-06
forum: General Help
---

### Post by markp1989 on 2007-12-06
i am setting up my media pc to boot from CF card, with geexbox and ubuntu installed on it, i was wondering if there is a way to move /tmp to a ram disk to help reduce CF wear and tear?

---

### Post by rshetye on 2007-12-06
you will need to create an entry in /etc/fstab to mount /tmp as a tmpfs, with an associated max size (and max number of entries optionally).

---

### Post by markp1989 on 2007-12-06
so id have to have somthing like ```
tmpfs     /tmp .....
``` ? right, can you give me a few more details what i would have to write? the computer only had 256mb of ram, so i dont know what a suitable max size wud be ?

---

### Post by markp1989 on 2007-12-07
tmpfs /tmp tmpfs rw 0 0 

i added that to my fstab file, and it worked ok, is that the correct way to do it?

---

### Post by motin on 2008-01-21
This seems to be more appropriate:

```
# /tmp as a temporary file system
none /tmp tmpfs size=2G,nr_inodes=200k,mode=01777 0 0

```

Source: [https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/18661](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/18661)

---

### Post by kerry_s on 2008-01-21
/tmp is already a ram folder out of the box, no need to set it up. that's why /tmp is always empty after a reboot.

---

### Post by motin on 2008-01-21
> **kerry_s said:**
> /tmp is already a ram folder out of the box, no need to set it up. that's why /tmp is always empty after a reboot.

Oh I didn't know that /tmp was configured without using /etc/fstab. I had no /tmp as a ramdisk showing up when issuing "df", and after I added the above to /etc/fstab and a:

```
sudo -s
mv /tmp /tmp-org
umount /tmp
mkdir /tmp
mount -a
mv /tmp-org/* /tmp/
mv /tmp-org/.* /tmp/
```

(Or a reboot)

then /tmp is shown as it's own ramdisk again.

---

### Post by kerry_s on 2008-01-21
yeah, it's mounted with a different program, the same program that does the processor, usb's, drivers, etc... look in /etc/mtab.

---

### Post by dagnabit dang doohickey on 2008-01-22
> /tmp is already a ram folder out of the box, no need to set it up. that's why /tmp is always empty after a reboot.
/tmp is on disk and gets cleaned on boot. This behavior can even be adjusted by specifying how many days to keep files in /tmp before cleanup.

---

### Post by kerry_s on 2008-01-22
> **dagnabit dang doohickey said:**
> /tmp is on disk and gets cleaned on boot. This behavior can even be adjusted by specifying how many days to keep files in /tmp before cleanup.

okay, that makes more sense.

---

### Post by anystupidname on 2008-02-12
> **dagnabit dang doohickey said:**
> /tmp is on disk and gets cleaned on boot. This behavior can even be adjusted by specifying how many days to keep files in /tmp before cleanup.

noob question: how/where exactly do you set the number of days?

Is it easily possible to do this with the Trash as well or just simply add the Trash to /tmp?

---

