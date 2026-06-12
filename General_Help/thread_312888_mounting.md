---
title: "mounting"
date: 2006-12-05
forum: General Help
---

### Post by aco on 2006-12-05
is there something like daemon tools to mount images of all kinds in ubuntu

---

### Post by taurus on 2006-12-05
What kind of images are you talking about?  You can mount iso with

```
sudo mount -t iso9660 -o loop filename.iso <mount point>
```
And if you have cue/bin, you can use bin2iso to convert it to iso and use the command above to mount it...

---

### Post by aco on 2006-12-05
how would i mount image from alcohol120% called *.mdf and *.mds

---

### Post by CatKiller on 2006-12-05
> **aco said:**
> how would i mount image from alcohol120% called *.mdf and *.mds

[http://packages.ubuntu.com/dapper/misc/mdf2iso](http://packages.ubuntu.com/dapper/misc/mdf2iso)

> mdf2iso is a very simple utility to convert an Alcohol 120% mdf image to an iso, toc / dat or cue / bin image.

---

