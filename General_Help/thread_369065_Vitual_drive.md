---
title: "Vitual drive"
date: 2007-02-24
forum: General Help
---

### Post by ali780 on 2007-02-24
Hello
I need a virtual drive software for mounting ISO file. Could somebody introduce me suh software?
Thanks

---

### Post by nereid on 2007-02-24
You don't need one. Just mount your ISO file

```

mount -t iso9660 -o loop /path/to/your.iso /path/to/the/target/directory

```

This could look like this for example (ubuntu.iso is the iso file in your home directory and /media/cdrom is the target directory)

```

sudo "mount -t iso9660 -o loop ~/ubuntu.iso /media/cdrom"

```

Don't forget the quotes if you use sudo!

---

### Post by louis_nichols on 2007-02-24
Actually, in Linux you don't need any software like that, because you can just mount an ISO file as a loopback device. So just make a folder where you wish to mount it, then use:

~# mount -o loop -t iso9660 *path-to-iso-file* *path-where-you-want-to-mount-it*

---

### Post by ali780 on 2007-02-24
Thank you.

---

### Post by Pitt Stains on 2007-04-19
This didn't do exactly what I hoped it would (i.e., cause Ubuntu to treat the mounted ISO as a CD/DVD device).  Now I've got this cdrom0 folder in my media directory and I can't make it go away.  If I try to sudo chmod or chown it, Ubuntu tells me it's a read-only file system.

How do I make it go away?

---

