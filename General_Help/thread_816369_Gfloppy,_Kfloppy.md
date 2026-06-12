---
title: "Gfloppy, Kfloppy"
date: 2008-06-02
forum: General Help
---

### Post by stevejeep on 2008-06-02
Always whenever I format a 1.44 floppy, G and K floppy formats it to 1.3mb using ext2. Dos formats to 1.4mb. Tried several disks, different formats all the same. Trying to copy super_grub_disk @ 1.4mb and says not enough space. This occurred with 6.06 Dapper and now with 7.1 Gusty. Have never been able to format to 1.44 floppy. Legacy FD; Sony MFD-2HD floppies.

---

### Post by plucky on 2008-06-03
Try this in a terminal window

```
dd if=name_of_floppy.img of=/dev/fd0
```

Terms:-
dd=convert and copy
if=input file
of=output file
device=/dev/fd0       :zero not letter O
name of floppy image=super_grub_disk_english_floppy_0.9716.img


Floppy image copied from [this website](http://supergrub.forjamari.linex.org/?section=download).Choose your language and modify the name of floppy as appropriate.

Good Luck

---

