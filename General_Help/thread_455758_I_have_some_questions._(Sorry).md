---
title: "I have some questions. (Sorry)"
date: 2007-05-26
forum: General Help
---

### Post by Crafty Kisses on 2007-05-26
First off, I really don't have a program that can burn ISO's (My Nero Trial ran out) and secondly I wanted to switch to Ubuntu 7.04 with the recent problems I've been having with 6.06 Dapper, any good programs that can burn ISO's? For Free.

---

### Post by yabbadabbadont on 2007-05-26
> K3B
That is usually the one that is suggested first.

---

### Post by DoktorSeven on 2007-05-26
Nicest CD burner (burns ISOs, music, data, etc) is **k3b** in my opinion, but there are lots of other programs in Linux that can do so as well.  

There's even a commandline CD burner for ISOs and such: **wodim**

---

### Post by mitch.c on 2007-05-26
Kubuntu: K3b
Gnome: Gnomebaker
CLI:
```
# speed and dev match my drive, your's may be different.
$ cdrecord -v speed=48 dev=0,0,0 -data your.iso
```

---

### Post by reclusivemonkey on 2007-05-27
If you use Gnome, you can simply right click on an ISO and select "Write to Disc...".

---

### Post by Ocxic on 2007-05-27
there is a way to install without using a cd, I'll try to track down the link, brb..

here's how to dp it.. 
[https://help.ubuntu.com/7.04/installation-guide/i386/ch05s01.html#boot-initrd](https://help.ubuntu.com/7.04/installation-guide/i386/ch05s01.html#boot-initrd)

this it the guide i go it from.
[https://help.ubuntu.com/7.04/installation-guide/i386/index.html](https://help.ubuntu.com/7.04/installation-guide/i386/index.html)

---

### Post by Bakerman on 2007-05-27
As you refer to Nero, I assume you've still got access to Windows XP. There is a powertoy that adds ISO burning support to Win XP. You can find out more info here:

[http://isorecorder.alexfeinman.com/isorecorder.htm](http://isorecorder.alexfeinman.com/isorecorder.htm)

Never tried it myself, so I don't know if it's any good! It appears to be free anyway...

---

