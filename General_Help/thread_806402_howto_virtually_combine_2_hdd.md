---
title: "howto virtually combine 2 hdd"
date: 2008-05-24
forum: General Help
---

### Post by ikkubus on 2008-05-24
how can i combine 2 hdd?
im trying to mount hdd2 in a directory in hdd1. the problem is ,i cant see hdd1 content. is there any other way to do this? other than mount..

thanks

---

### Post by sdennie on 2008-05-24
You could use LVM or setup RAID but, it sounds like you can accomplish what you want simply using mount.  Are you sure you have the permissions setup right on what you are trying to mount?

---

### Post by ikkubus on 2008-05-25
yes, i have root access. LVM and raid ok ill read more about that. thanks

---

### Post by AnRa on 2008-05-25
[mhddfs: join several real filesystems together to form a single larger one](http://debaday.debian.net/2008/05/25/mhddfs-join-several-real-filesystems-together-to-form-a-single-larger-one/)

---

### Post by sdennie on 2008-05-25
You probably don't need to take those kinds of drastic steps.  If you post the contents of /etc/fstab (or the command you are using to mount) and /proc/mounts, I would imagine that someone can help you with the problem you are having with mount.

---

