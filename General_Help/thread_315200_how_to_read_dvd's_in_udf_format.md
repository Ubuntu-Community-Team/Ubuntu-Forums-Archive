---
title: "how to read dvd's in udf format?"
date: 2006-12-08
forum: General Help
---

### Post by batina on 2006-12-08
i recently installed ubuntu. i'm a total beginner in this whole linux thing. dont have any experience. :-k 

i created backups of my files in windows, burned them using UDF format... it seems that ubuntu cant read them... can someone help me? PLEASE!!![-o< [-o<

---

### Post by po0f on 2006-12-08
batina,

What does the /etc/fstab entry for your DVD drive look like?

---

### Post by Matt Yun on 2006-12-09
(assume that your dvd is device /dev/hdc)

mount -t udf /dev/hdc /media/dvd

See 'man mount' for more udf filesystem options

---

### Post by batina on 2006-12-09
people thanks a lot!!!!!

based on your answers, i did some experimenting, and fixed it!
thanks!!

---

