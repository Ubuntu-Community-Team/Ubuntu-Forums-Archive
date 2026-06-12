---
title: "External HD mount permissions"
date: 2008-03-05
forum: General Help
---

### Post by edm1 on 2008-03-05
I've searched for an answer but am unable to find one. I would like my ext HD to be mounted with 'Owner' having full access and 'Group' and 'Others' having read access only.

In gnome-mount the mount option is currently set to 'fmask=0077 dmask=0077' which gives Owner full access and the others none. I have tried other values (0000 and 0022) without success; i seem to lose ownership to root.

Can anyone shed light on the situation?

---

### Post by taurus on 2008-03-05
What is the filesystem of that external harddrive?

---

### Post by edm1 on 2008-03-05
vfat (fat 32)

The full mount options at the moment are

```
rw nosuid nodev uid=1000 fmask=0077 dmask=0077 codepage=cp437 iocharset=iso8859-1 shortname=mixed usefree utf8
```

---

### Post by edm1 on 2008-03-06
bump

---

