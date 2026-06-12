---
title: "Mounting Disk Images"
date: 2007-06-20
forum: General Help
---

### Post by SnakeByte29 on 2007-06-20
I was just wondering if there is a way to mount disk images (.iso, .cue, .bin, etc) in Ubuntu? What I'm looking for is a program that does essentially the same thing as DaemonTools.

---

### Post by taurus on 2007-06-20
Try bchunk.  It's in the repos.

[http://he.fi/bchunk/](http://he.fi/bchunk/)

```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop **filename.iso** /media/iso
```

---

### Post by CityofAsh on 2007-07-09
That works thanks!

---

