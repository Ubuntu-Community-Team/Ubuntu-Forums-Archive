---
title: "Booting from a copied partition"
date: 2007-03-08
forum: General Help
---

### Post by ppatalano on 2007-03-08
Is it possible to boot from a an ext3 partition that is copied to another location??? :confused:

---

### Post by nereid on 2007-03-08
Yes, you must install GRUB again in the master boot record and you must modify the fstab and the  menu.lst files to reflect the changes you've made to the partition layout.

---

### Post by ppatalano on 2007-03-08
I just have no clue how to reinstall GRUB. Thanks for the fast reply. :)

---

### Post by nereid on 2007-03-09
Run this

```

sudo grub-install

```

And make sure, that these files get changed. If you haven't done this you'll have to restart your pc and boot with a boot disk to change the files.

---

