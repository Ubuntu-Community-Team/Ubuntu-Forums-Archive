---
title: "Need help in setting up Multimedia"
date: 2005-07-08
forum: General Help
---

### Post by mail2sona938 on 2005-07-08
Im using a Mobile Intel 915 GM display adapter. But Im using a VESA driver. I installed Mplayer which wont play anything and XMMS which will also wont play MP3s. I installed Xine which plays every thing but it drops out too many frames when any VCD or DVDs are played. Could anyone help pls.

---

### Post by pvoce on 2005-07-08
[QUOTE=mail2sona938]Im using a Mobile Intel 915 GM display adapter. But Im using a VESA driver. I installed Mplayer which wont play anything and XMMS which will also wont play MP3s. I installed Xine which plays every thing but it drops out too many frames when any VCD or DVDs are played. Could anyone help pls.[/QUOTE]
 Firstly, mp3's are *audio* files, so you may wish to get LAME (an mp3 encoder) for the mp3 support, unless other players are playing them, in which case, look for an xmms plugin.

Secondly, try typing in console (as root) "hdparm -d1 /dev/(your dvd device)" to take care of the jerky playback:)

Hope this helps:)

---

### Post by titus1950 on 2005-07-08
[QUOTE=mail2sona938]Im using a Mobile Intel 915 GM display adapter. But Im using a VESA driver. I installed Mplayer which wont play anything and XMMS which will also wont play MP3s. I installed Xine which plays every thing but it drops out too many frames when any VCD or DVDs are played. Could anyone help pls.[/QUOTE]




Read this [http://ubuntuguide.org/](http://ubuntuguide.org/) it will help you.

---

### Post by mail2sona938 on 2005-07-10
I tried all that...but when I put on a VCD or a DVD, the video quality is very very poor compared to that of windows. I suspect my video driver is not good enough. I didnt install any drivers except my wireless. I just used dpkg-reconfigure to change the default driver to VESA. So any information or suggetions from this????

---

