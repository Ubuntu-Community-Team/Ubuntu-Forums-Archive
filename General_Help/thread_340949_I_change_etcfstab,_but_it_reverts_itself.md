---
title: "I change /etc/fstab, but it reverts itself"
date: 2007-01-17
forum: General Help
---

### Post by stevekl on 2007-01-17
I have two hard drives in this machine (Ubuntu sees them as hda and hdb), but I do NOT want any shares on hdb to be mounted at all, for various reasons.

I thought this would be no problem if I just put noauto in the file. But then the next time I restart, /etc/fstab is the same as it was before. Then I tried deleting the entries in /etc/fstab but a restart causes the file to revert.

What's causing this? Before anyone asks, yes I checked all the obvious stuff; the file is being changed (I check it with less or cat), I do have root permission while I do it, et cetera.

---

### Post by swamytk on 2007-01-18
udev is the system daemon which does this job of automatically detecting the file systems and mouting through /etc/fstab file.

---

