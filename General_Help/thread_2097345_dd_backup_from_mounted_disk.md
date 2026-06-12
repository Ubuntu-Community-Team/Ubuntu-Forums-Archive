---
title: "dd backup from mounted disk ?"
date: 2012-12-22
forum: General Help
---

### Post by daKoolaid on 2012-12-22
[FONT=FreeSans]Will the image create and restore properly if the root partition is mounted or does this have to be done from a live session?[/FONT]

---

### Post by sudodus on 2012-12-22
The risk is very high that the content of the drive will change during the cloning process, and you will get an inconsistent (bad) image, if the drive is mounted. This is particularly so with the system (root) partition /.

So you must boot from another drive and avoid mounting any partition of a drive, that is being cloned or imaged.

It can certainly be done with dd, but it is nicknamed 'disk destroyer', because it does what it is told, instead of doing what you intended to do. It is very powerful and does not ask naughty questions.

So I would recommend ***Clonezilla*** instead for cloning and imaging of drives and partitions. Clonezilla asks twice, so it is safer, and it uses partclone, which is more efficient than dd + gzip. It does not copy unallocated disk space, and it can repair bad ext file systems and it can check that an image is restorable.

---

### Post by coldcritter64 on 2012-12-22
If you do use dd, I recommend to unmount the partition/device being copied and if root/home is involved do it from a live session. Use dd with great care, it is very unforgiving of mistakes.
+1, to the nickname "data destroyer" and the clonezilla recommendation from sudodus.

---

### Post by daKoolaid on 2012-12-23
Thanks guys. I was hoping to have something that can do it with the system booted but I guess no. Downloading Clonezilla now.

---

### Post by sudodus on 2012-12-23
Well, you can run a backup of files with your normal system running. This is often done every night or once every week at companies and institutions. But that is different from making exact images of the drive(s). There are special software packages for that purpose.

---

