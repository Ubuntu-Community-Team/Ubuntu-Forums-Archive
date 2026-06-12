---
title: "Find command error!!! What am i doing wrong?"
date: 2007-12-21
forum: General Help
---

### Post by phillips321 on 2007-12-21
Hi guys,

for some reason i cant get the following command to work. have i just made a stupid mistake?

```
phillips321@LinuxDesktop:/media/data/Music/Extra$ find . -name *.rar - print
find: paths must precede expression
Usage: find [-H] [-L] [-P] [path...] [expression]

phillips321@LinuxDesktop:/media/data/Music/Extra$ 

```

cheers guys

---

### Post by K.Mandla on 2007-12-21
This is probably more complicated than necessary, but it seems to work for me.

```
find `pwd` -name "*.rar"
```
Does that help at all?

---

