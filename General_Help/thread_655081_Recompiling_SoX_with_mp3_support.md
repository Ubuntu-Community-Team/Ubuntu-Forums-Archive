---
title: "Recompiling SoX with mp3 support"
date: 2007-12-31
forum: General Help
---

### Post by bryanosaurus on 2007-12-31
I'm trying to use SoX to convert some .ogg files to .mp3
I know this is possible, as this site has a guide to doing it:

[http://www.linuxweblog.com/convert-ogg-to-mp3](http://www.linuxweblog.com/convert-ogg-to-mp3)

Since SoX doesnt have mp3 support I need to install a version which enables it.The problem is that I can't use rpm on Ubuntu.
I'm not sure how to go about this. After downloading the rpm which is SoX with lame/mp3 enabled, I'm stuck. I think I need to use alien? Any help would be appreciated.

rpm -Uvh sox-12.17.5-3.fr.i386.rpm

---

### Post by wladimir on 2008-01-17
did you try 
```
sudo alien filename
```

or just have a look at 
```
man alien
```

---

