---
title: "screen recording software? gtkrecordmydesktop is very slow for me"
date: 2008-03-05
forum: General Help
---

### Post by ogwilson on 2008-03-05
Hi. I tried using gtk-recordmydesktop but the outputted video is laggy, the sound isn't synched up right, and its just overall terrible quality. It doesnt even allow me to select a specific dimensional region to record in. Anyone have any other GOOD programs?

---

### Post by Vadi on 2008-03-05
I believe by default, gtk-recordmydesktop captures at 15FPS. Which to the human eye, makes the video laggy - you'd want it at 25, that makes it smoother.

(don't know about other programs, I only use this one heh)

---

### Post by jespdj on 2008-03-06
Try [Istanbul](http://live.gnome.org/Istanbul). You should be able to install it from the Ubuntu repository:
```
sudo apt-get install istanbul
```

---

### Post by Vadi on 2008-03-06
I gave istanbul a try, but I only achieved viewable video quality when I set the resolution to be a quarter, so the video was just smaller than the youtube ones.

So I decided to investigate - and it looks like the version of gtk-recordmydestkop in ubuntu repositories is extremely old. Since then, there were many new versions of it fixing, and adding quite a lot of things. You can get a newer version off getdeb.net, but it's still not up to date there - I filed a bug report on their launchpad though, so hopefully we'll have the latest version of the program working.

---

### Post by Rytron on 2008-03-06
try [XVidCap]("http://xvidcap.sourceforge.net/")

hope this helps.

---

