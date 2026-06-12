---
title: "Desktop Capture Video"
date: 2006-11-05
forum: General Help
---

### Post by krypto_wizard on 2006-11-05
Hi,

I want to capture my desktop activities in a video like some people have posted it on youtube or google videos.

Can you please tell me what application to use it in KDE and Gnome to capture the desktop.

Thanks,

---

### Post by taurus on 2006-11-05
Perhaps istanbul is what you have in mind!

---

### Post by krypto_wizard on 2006-11-06
Exactly, but its quality is not as good as some of the others I have seen. It brings in lot of jitters.

---

### Post by aysiu on 2006-11-06
Have you tried Xvidcap?
[http://xvidcap.sourceforge.net/](http://xvidcap.sourceforge.net/)

---

### Post by spockrock on 2006-11-06
if you use beryl there is a video capture plugin.

---

### Post by Cable on 2006-11-06
I've heard good things about [recordMyDesktop]("http://recordmydesktop.sourceforge.net/") as well.

---

### Post by towsonu2003 on 2006-11-06
> **taurus said:**
> Perhaps istanbul is what you have in mind!

istanbul is real buggy (100% cpu usage, reported) on my system, so be careful ;)

---

### Post by loell on 2006-11-07
try the two deb packages for edgy

[recordmydesktop deb packages]("http://www.yourfilelink.com/get.php?fid=207990")

extract and install

the first deb is the command line and the other is the gtk front end

to upload your videos in youtube and other sites

you should convert the default ogg video format to avi by

```
mencoder -idx myvideo.ogg -ovc lavc -oac mp3lame -o myvideo.avi
```

---

### Post by loell on 2006-11-07
my boring youtube video demo ;) 

with xara lx samples

[http://www.youtube.com/watch?v=_6OlnyEKlXY]("http://www.youtube.com/watch?v=_6OlnyEKlXY")

captured with gtk-recordmydesktop :mrgreen:

---

