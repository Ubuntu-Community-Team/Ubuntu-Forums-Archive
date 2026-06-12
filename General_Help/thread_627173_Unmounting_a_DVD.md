---
title: "Unmounting a DVD"
date: 2007-11-29
forum: General Help
---

### Post by enchance on 2007-11-29
My DVD mounts itself automatically when I place in a DVD movie. Just a thought, but how to I unmount it? Do I go 
```
$ umount /media/cdrom/
```
Thanks.

---

### Post by PmDematagoda on 2007-11-29
Yes, but I believe you will have to append your command with sudo to make it work, and the cdrom will have to have the number of the CDROM in which the DVD is found in, if it is the first one then cdrom is cdrom0.

---

### Post by enchance on 2007-11-29
I got it.
```
$ sudo umount /dev/cdrom/
```

---

### Post by PmDematagoda on 2007-11-29
Hmm, from what I have seen, the command is actually your first one. But whatever works for you is what you want:).

---

