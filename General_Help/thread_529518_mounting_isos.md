---
title: "mounting isos?"
date: 2007-08-19
forum: General Help
---

### Post by duaneb on 2007-08-19
On OSX, I just double click and it mounts, but on ubuntu, it opens in the Archive manager :P. How can I, as an unprivileged user, mount a .iso?

---

### Post by taurus on 2007-08-19
Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
ls -la /media/iso
```

---

### Post by ruibernardo on 2007-08-19
To make what taurus said in a more graphical way, you can try this [Howto]("http://ubuntuforums.org/showthread.php?t=87369") from "Tips & Tutorials" forum, or this [webpage]("http://www.debianadmin.com/mount-and-unmout-iso-images-without-burning-them.html") from debianadmin.com.

---

