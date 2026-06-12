---
title: "error while loading shared libraries: libavformat.so.55"
date: 2014-07-03
forum: General Help
---

### Post by tomatito2 on 2014-07-03
Hi there, 

I have removed Blender: 
```
sudo apt-get remove blender
```

After that I made a new install using the software centre. When I tried to start Blender I received this message: 
```
tomatito@tomatito-OptiPlex-745:~$ blender 
/usr/lib/blender/blender: error while loading shared libraries: libavformat.so.55: cannot open shared object file: No such file or directory

```

**I need some help/advice to solve this problem. Thanks in advance.**

---

### Post by mc4man on 2014-07-04
post - 
```
apt-cache policy blender 
```

---

### Post by tomatito2 on 2014-07-04
Thanks! 

```
tomatito@tomatito-OptiPlex-745:~$ apt-cache policy blender
blender:
  Geïnstalleerd: 2.71~git201406121839.169c95b-0irie1~precise1
  Kandidaat:     2.71~git201406121839.169c95b-0irie1~precise1
  Versietabel:
 *** 2.71~git201406121839.169c95b-0irie1~precise1 0
        500 http://ppa.launchpad.net/irie/blender/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     2.62-1 0
        500 http://nl.archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages

```

**What does this mean/what to do now? **

---

### Post by mc4man on 2014-07-04
Blender from that ppa depends on & uses it's own set of ffmpeg shared libs provided by the ppa's blender-codecs-ffmpeg2.2 package, it it installed?
The libs would be found in /usr/lib/blender/ffmpeg/2.2/lib/

---

### Post by tomatito2 on 2014-07-04
> it it installed?
No 
```
tomatito@tomatito-OptiPlex-745:/usr/lib/blender$ ls
2.67             blenderplayer           datatoc          Python-license.txt
blender          blender.svg             GPL-license.txt  readme.html
blender.1        blender-thumbnailer.py  makesdna         reset_excepthook.py
blender.desktop  copyright.txt           makesrna         scripts

```

Im realy a noob about this subject. So what to do? 
(I only know this: Blender installed by using the software centre should work out of the box :confused:)

---

