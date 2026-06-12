---
title: "Trying to extract files from a DVD image"
date: 2007-11-14
forum: General Help
---

### Post by je1117 on 2007-11-14
I am trying to extract the files from a dvd ISO I have. I hear acetone is pretty good, any other suggestions?

---

### Post by taurus on 2007-11-14
If it's an ISO image, then you can just mount it and copy whatever you want from it.

```
sudo mkdir /media/iso
sudo mount -t iso9660 **filename.iso** /media/iso -o loop
ls -la /media/iso
```

---

### Post by je1117 on 2007-11-14
Well, I thought maybe that was only for CDs and not DVDs. Whenever I do any and all variations of that commands it says:

mount: Not a directory

But /media/iso is a directory on my filesystem. This is where it doesn't make any sense to me...

---

### Post by taurus on 2007-11-14
What is the exact command that you ran?

---

### Post by zaphod777 on 2007-11-14
here is a GUI front end

GMountISO

you can mount the iso and copy the files off.

---

### Post by sinaen on 2008-02-06
sudo mount -t iso9660 Black.iso /media/iso/ -o loop
mount: Not a directory

---

