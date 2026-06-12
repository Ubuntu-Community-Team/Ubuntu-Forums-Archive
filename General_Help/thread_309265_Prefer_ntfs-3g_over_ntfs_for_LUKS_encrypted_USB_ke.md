---
title: "Prefer ntfs-3g over ntfs for LUKS encrypted USB key"
date: 2006-11-29
forum: General Help
---

### Post by thm on 2006-11-29
Hi all,

I have tried using ntfs on a LUKS encrypted usb key.  Setting it up works fine.  When plugging in the key I get asked for the password.  It even gets mounted, unfortunately as ntfs instead of ntfs-3g (which I have installed, non-LUKS volumes work fine, the same key just formatted with mkntfs gets mounted as ntfs-3g).  Any hints on where I could say "prefer ntfs-3g over ntfs" for a LUKS volume?

I have Ubuntu Edgy Eft installed with packages ntfs-3g and pmount from 

deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) dapper main main-all

which I have read in [uwiki]ntfs-3g[/uwiki].

---

### Post by thm on 2006-12-03
This was solved by givré in [post]1835207[/post] with a new package for pmount: pmount_0.9.13-1givre4.  Thanks givré.

---

