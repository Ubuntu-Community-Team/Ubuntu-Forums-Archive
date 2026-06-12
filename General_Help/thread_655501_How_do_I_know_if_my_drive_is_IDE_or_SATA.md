---
title: "How do I know if my drive is IDE or SATA"
date: 2008-01-01
forum: General Help
---

### Post by jakey123 on 2008-01-01
:popcorn: Well hello there Ubuntu users how do I know if my drive is a IDE or A SATA. I run windows XP is there a way in the bios or under windpws can you take it easy on me.

---

### Post by tronica on 2008-01-01
I believe under device manager it will tell you what it is.

---

### Post by HermanAB on 2008-01-01
Type this:
$ mount

SATA drives are listed as sdx and IDE drives as hdx.

Cheers,

Herman

---

### Post by ~LoKe on 2008-01-01
This will do it as well:
```
sudo fdisk -l
```

**SATA**
/dev/sda
/dev/sdb
/dev/sdc

**IDE**
/dev/hda
/dev/hdb
/dev/hdc
/dev/hdd

---

