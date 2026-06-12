---
title: "mount a cd"
date: 2008-05-07
forum: General Help
---

### Post by afreet5 on 2008-05-07
how could mount a cd without buring it ??

---

### Post by wrgb2 on 2008-05-07
It should be mounted automatically when you insert the cd into the drive - are you sure its a good cd?

---

### Post by tacutu on 2008-05-07
do you mean a CD image? i.e. a iso file?

---

### Post by Lord Xeb on 2008-05-07
Go to Computer and right click on cd/dvd rom drive and select "mount volume"

---

### Post by afreet5 on 2008-05-10
it's a cd image (iso)

---

### Post by zvacet on 2008-05-10
Install [gmountiso]("http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html").

---

### Post by ChompTheMan on 2008-05-10
You could also open a terminal and type in:

```
sudo mount -t iso9660 filename.iso /media/mount -o loop
```

/media/mount is my mount point.  You can make your mount point wherever you like.  To unmount type in:

```
sudo umount /media/mount
```

---

