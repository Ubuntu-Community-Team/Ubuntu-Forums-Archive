---
title: "How to copy encrypted files by Encfs"
date: 2015-11-29
forum: General Help
---

### Post by HPCTECH on 2015-11-29
Hi,

Whenever I try to copy files encrypted by Encfs I got **"failed: File name too long (36)"** !

I tried to copy using cp and rsync both of them failed!

The full log of rsync is: [https://paste.kde.org/pkkasicb5](https://paste.kde.org/pkkasicb5)

NOTE: File system of both source and target disks is EXT4.

---

### Post by matt_symes on 2015-11-29
Hi

> **HPCTECH said:**
> Hi,

Whenever I try to copy files encrypted by Encfs I got **"failed: File name too long (36)"** !

I tried to copy using cp and rsync both of them failed!

The full log of rsync is: [https://paste.kde.org/pkkasicb5](https://paste.kde.org/pkkasicb5)

NOTE: File system of both source and target disks is EXT4.

This looks to be a bug in encfs. 

You may want to read this at it relates to your problem.

[https://github.com/bit-team/backintime/issues/445](https://github.com/bit-team/backintime/issues/445)

Kind regards

---

### Post by HPCTECH on 2015-11-30
Yes, This is a bug in Encfs as mentioned in their repository
[https://github.com/vgough/encfs/issues/7](https://github.com/vgough/encfs/issues/7)

---

