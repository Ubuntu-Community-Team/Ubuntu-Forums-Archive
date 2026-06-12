---
title: "LVM on ubuntu"
date: 2022-01-31
forum: General Help
---

### Post by tashman89 on 2022-01-31
Hello Dears,

Could you please advise why in some of ubuntu version I cant use LVM during installation the OS, there is no option to select LVM, and please advise when we have to use LVM and when we have to use standard .


BR

---

### Post by HermanAB on 2022-01-31
LVM is an advanced layer on top of the regular Linux partition system.  It is especially useful for servers where the disk usage is expected to grow over time.  It provides the ability to add disks and make snapshots for example.  It is not really useful for home users or for simple servers that will more or less stay the same forever.

---

