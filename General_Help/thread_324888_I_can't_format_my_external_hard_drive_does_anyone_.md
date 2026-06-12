---
title: "I can't format my external hard drive does anyone know how?"
date: 2006-12-24
forum: General Help
---

### Post by thenetduck on 2006-12-24
Hi, 
  I have a 160GB External Hard drive. Currently it is formated in two parts. An apple part and windows part. When I tried to use Gparted to format it to a single ext3 format, it doesn't even give me the option to delete the partitions. It also has locks on the side. How can I get ride of the lock and format my external hard drive? Thanks, 

 The Net Duck

---

### Post by matthew on 2006-12-24
My first thought is the drive is probably mounted and you can't format or partition a mounted volume. Look in gparted for an "unmount" option. Try that first and see if once you unmount the drive you are allowed to partition/format as you like.

---

### Post by chaitanyamisal on 2008-05-13
Thanks mate ... 

i came across such problem too, I was able to fix it ! 

--CM

---

