---
title: "how do you extract an initrd?"
date: 2007-06-29
forum: General Help
---

### Post by gnychis on 2007-06-29
Hi, how can i extract my initrd from my /boot to see whats in it? i gunzip''ed it, now 'file' says its an ASCII cpio archive

---

### Post by mpeters on 2007-06-30
Try the following:

[FONT="Fixedsys"][INDENT]mkdir initrd[/INDENT]
[INDENT]cd initrd[/INDENT]
[INDENT]gunzip < /boot/initrd.img-version |cpio -i --make-directories[/INDENT]
[INDENT]ls[/INDENT][/FONT]

---

