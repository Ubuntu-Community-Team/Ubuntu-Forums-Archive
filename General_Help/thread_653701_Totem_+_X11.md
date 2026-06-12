---
title: "Totem + X11 ??"
date: 2007-12-30
forum: General Help
---

### Post by Cygoku on 2007-12-30
How can I possibly set Totem video player to use X11 video rendering?

Cygoku

---

### Post by Cygoku on 2008-01-07
*bump*

---

### Post by Cygoku on 2008-01-21
*bump*

---

### Post by sdowney717 on 2008-04-27
[http://groups.google.com/group/linux.debian.user/browse_thread/thread/52390fc67564f4f4/8451bb82901b8d90?lnk=st&q=totem+x11#8451bb82901b8d90](http://groups.google.com/group/linux.debian.user/browse_thread/thread/52390fc67564f4f4/8451bb82901b8d90?lnk=st&q=totem+x11#8451bb82901b8d90)

[http://www.yvesvanbelle.net/DebianEtchInstall.html](http://www.yvesvanbelle.net/DebianEtchInstall.html)

I tried editing totem_config and xine_config BUT it makes no difference

If you use totem gstreamer, I think you can run gstreamer-properties and set video out to x11 xshm.
Select Video and change Default Output Plugin to X Window System (No Xv).

If you use totem-xine I cant figure it out.

This link says it works for totem-xine but I still get a black screen
xine does play fine, totem-xine does not
IF I turn off compiz, then I see the video in totem-xine

[http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html](http://www.ubuntugeek.com/fix-for-video-playback-problem-in-compiz-fusion.html)

---

