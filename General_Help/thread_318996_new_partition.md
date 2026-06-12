---
title: "new partition"
date: 2006-12-14
forum: General Help
---

### Post by kens8 on 2006-12-14
I just deleted my Windows directory (I never use Windows anyway.  Why keep it around?) and formatted it as an ext3 partition.  How do I get Ubuntu to recognize and mount this partition automatically on startup?  I am using Edgy.  Thanks.

---

### Post by aysiu on 2006-12-14
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) should help.

---

### Post by rafemonkey on 2006-12-14
if you add the drive to your /etc/fstab. (try `man fstab`) you can mount it (try `man mount`). I bet there is some nice gui way to do this, but I don't know it :(

---

### Post by aysiu on 2006-12-14
> **rafemonkey said:**
> I bet there is some nice gui way to do this, but I don't know it :( It's called Knoppix. Or Mepis.

---

