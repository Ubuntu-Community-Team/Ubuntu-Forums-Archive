---
title: "How to unzip *.zip.001 *.zip.002 files?"
date: 2007-07-29
forum: General Help
---

### Post by yinglcs2 on 2007-07-29
Hi,

Can you please tell me how to unzip *.zip.001 *.zip.002 files on ubuntu?  I try archieve manager with unrar, it does not work for me.

Thank you.

---

### Post by tbroderick on 2007-07-29
Install lxsplit. 

[http://ubuntuforums.org/showthread.php?t=332933](http://ubuntuforums.org/showthread.php?t=332933)

```
lxsplit -j archive.zip.001
unzip archive.zip
```

---

### Post by scxtt on 2007-07-29
you could probably do:

if you have 10 files,
cat *.zip.001 *.zip.002 . . . *.zip.010 > *.zip

---

