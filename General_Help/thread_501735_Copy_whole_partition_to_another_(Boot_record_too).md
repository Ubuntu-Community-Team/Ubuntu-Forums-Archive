---
title: "Copy whole partition to another (Boot record too)"
date: 2007-07-15
forum: General Help
---

### Post by trunks14 on 2007-07-15
IS there any program or command that will allow me to copy an entire partition (boot record too) to another partition?
I'm specially interested in the ability to copy a NTFS partition.

will dd suffice my needs?

---

### Post by Mr. C. on 2007-07-15
```
$ man dd
```

Exampe:

```
# dd if=/dev/sda1 of=/dev/sda2 bs=1M
```

MrC

---

