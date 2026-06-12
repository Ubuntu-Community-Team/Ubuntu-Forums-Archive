---
title: "Mount Images"
date: 2007-05-21
forum: General Help
---

### Post by Muffy on 2007-05-21
How can I use an IMG file on Ubuntu?

---

### Post by DoctorMO on 2007-05-21
Try this:

```
mkdir /tmp/iso; mount -t iso9660 disk.img /tmp/iso -o loop
```

---

### Post by apjone on 2007-05-21
mount -t iso9660 disc.img /mnt -o loop

---

### Post by Muffy on 2007-05-21
What should I do if I run into this error:

```
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by DoctorMO on 2007-05-21
that means it's not an iso file, and I think you might be out of luck because it may be some other format such as HFS+ (is it mac by the way?)

---

### Post by Muffy on 2007-05-21
I'm trying to mount a file with an .img extension. Its a Windows file.

---

