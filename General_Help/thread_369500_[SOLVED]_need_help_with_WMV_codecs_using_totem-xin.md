---
title: "[SOLVED] need help with WMV codecs using totem-xine"
date: 2007-02-24
forum: General Help
---

### Post by unebaguettesvp on 2007-02-24
so, i have totem-xine working great. it plays divx just fine. now i want it to play Windows Media files. how do i do it?

this is what i've tried so far:

[http://ubuntuos.wordpress.com/2006/08/01/howto-play-windows-media-video-wmv-in-ubuntu/](http://ubuntuos.wordpress.com/2006/08/01/howto-play-windows-media-video-wmv-in-ubuntu/)

it still gives the same error message. any help?

---

### Post by r4ik on 2007-02-24
Try,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Codecs)

Good luck !

---

### Post by bigken on 2007-02-24
look at automatix

---

### Post by r4ik on 2007-02-24
Automatix up again ?
When did that happened ?

---

### Post by bigken on 2007-02-24
didnt know it was down ?

---

### Post by r4ik on 2007-02-24
For over a day now.

[http://www.ubuntuforums.org/showthread.php?t=368472&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=368472&highlight=automatix)

---

### Post by unebaguettesvp on 2007-02-24
ok well according to the ubuntuguide.org wmv9 files can only play using vlc with amd 64 architecture. i would REALLY like for Totem to play all my video files. is there any way to set a parameter in totem to look for the codecs in /usr/lib/win32????

and automatix is down. does automatix work on amd 64?

---

### Post by unebaguettesvp on 2007-02-25
surely someone has been able to play windows media files on ubuntu 6.10 with amd 64 arch using totem-xine. there has to be some kind of configuration files i could change to point to the correct codecs.

help? any ideas?

i'm a linux newbie, almost 4 days now, and i find it extremely frustrating to deal with all of these codecs. why is this such a problem?

---

### Post by r4ik on 2007-02-25
Switch to Mplayer seems to work read,

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28Mplayer.29_with_plug-in_for_Mozilla_Firefox)

Good luck !

---

### Post by r4ik on 2007-02-25
Some info i found,

my desktop is an AMD64 which also lacks flash support so I use the package libflash-mozplugin which is the Gnash (GNU Flash Player) package, its isn't 100% flash9 compliant and is still under heavy development, but its a step in the right direction and I believe it is currently fully flash7 compliant so it will atleast get you around the net. Its not perfect and will from time to time crash out firefox, but its better than nothing and I assume once it goes stable, life will be good.

---

