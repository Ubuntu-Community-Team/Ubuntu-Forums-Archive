---
title: "Problem with SieFS"
date: 2005-06-18
forum: General Help
---

### Post by Paool on 2005-06-18
Hi there :D

I have fuse 2.2.1 module in kernel, compiled SieFS 0.5 and when I mounted my CX65 it doesn't wrok :( (no errors while mounting)

```
sudo mount -t siefs /dev/ttyS0 /media/mobile
```

It creates a file, which I can't open :(

[[img]http://img78.echo.cx/img78/6295/zrzutekranu4vo.th.png[/img]](http://img78.echo.cx/my.php?image=zrzutekranu4vo.png)

anyone know what I should do?

---

### Post by kamstrup on 2005-08-21
Searching the web for Siemens CX65 stuff for Linux, and decided to give the Ubuntuforums a try to...

Sad to hear, but don't SieFS website say that SieFS needs a 2.4 kernel? If you are indeed running a 2.4 kernel, you should know that Gnome will prolly not function properly (it needs 2.6 kernel for HAL...)

Have you had any progress on this? How about ls'ing /mnt/mobile from the command line?

**Resources:**
SieFS - [http://chaos.allsiemens.com/siefs/](http://chaos.allsiemens.com/siefs/)
FUSE - [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)

---

### Post by kamstrup on 2005-08-23
[QUOTE=kamstrup]Searching the web for Siemens CX65 stuff for Linux, and decided to give the Ubuntuforums a try to...

Sad to hear, but don't SieFS website say that SieFS needs a 2.4 kernel? If you are indeed running a 2.4 kernel, you should know that Gnome will prolly not function properly (it needs 2.6 kernel for HAL...)

Have you had any progress on this? How about ls'ing /mnt/mobile from the command line?

**Resources:**
SieFS - [http://chaos.allsiemens.com/siefs/](http://chaos.allsiemens.com/siefs/)
FUSE - [http://fuse.sourceforge.net/](http://fuse.sourceforge.net/)[/QUOTE]
 Somebody seems to have got it working:

[http://www.ubuntuforums.org/showthread.php?p=314519#post314519](http://www.ubuntuforums.org/showthread.php?p=314519#post314519)

---

