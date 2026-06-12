---
title: "mounting an iso?"
date: 2007-05-27
forum: General Help
---

### Post by marshall.robert on 2007-05-27
hello,
im in a situation where i cant get the internet on ubuntu and i want to do a cd upgrade, but i dont want to burn a cd.
my question is; what is the best method/program to use to mount an iso?
all sugestions will be greatfully appreciated :D

-rob

---

### Post by jgoguen on 2007-05-27
```
mount -t iso9660 -o loop /path/to/iso /mnt
```
That will mount the ISO on /mnt (assuming nothing else is mounted there already) and you can access it just like if you burned the CD.

---

### Post by dan171717 on 2007-05-27
u can get free cds of ubuntu shiped to your door

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by dan171717 on 2007-05-27
u can get free cds of ubuntu shiped to your door

[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

---

### Post by marshall.robert on 2007-05-27
cheers, ill try that code.

and my mate said it took a month to get the disk and i cant be arsed to wait that long, lol. maybe one day

-rob

---

