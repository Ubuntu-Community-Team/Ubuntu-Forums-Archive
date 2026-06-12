---
title: "Updating without cd"
date: 2007-03-03
forum: General Help
---

### Post by bobjr777 on 2007-03-03
i dont have a cd drive in my server anymore. when i try to intall apache it asks for the cd. how can i get it to download the package insted of getting it from the cd. or how can i mount the cd and install off and iso.

---

### Post by taurus on 2007-03-03
You need to edit /etc/apt/sources.list

```
sudo nano -Bw /etc/apt/sources.list
```
and place a # in front of the line that has CDROM in it, usually the first line.  Then, save it and exit with <Ctrl>o and <Ctrl>x.

Then, run

```
sudo aptitude update
```
Now, install whatever you need and it won't ask you to insert the CD anymore.

---

### Post by bobjr777 on 2007-03-03
Thanks for you help works great
it was the second line i had to change

---

