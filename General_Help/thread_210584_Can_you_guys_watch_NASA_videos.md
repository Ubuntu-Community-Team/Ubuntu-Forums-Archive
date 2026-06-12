---
title: "Can you guys watch NASA videos?"
date: 2006-07-07
forum: General Help
---

### Post by tommcd on 2006-07-07
I have pretty much every codec installed but when I try to watch videos here:
[http://www.jpl.nasa.gov/multimedia/](http://www.jpl.nasa.gov/multimedia/)
I get sound, but no video. They seem to use flash. I can watch most flash videos, but not at nasa. Also here:
[http://www.killsometime.com/Video/Videos.asp](http://www.killsometime.com/Video/Videos.asp)
again, sound but no video.
Can anybody watch these? and know what I need to watch them? Any help appreciated, thanks!

---

### Post by Jagot on 2006-07-07
Nasa's videos require Flash 8, which is not made for Linux.  There are various workarounds, such as running the Windows version of Firefox in Wine and installing Flash with that.  Nasa do provide a downloadable mp4 file so it's watchable, albeit not so conveniently.

The second link works fine for me - have you followed this guide to setting up your media stuff:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by yopnono on 2006-07-07
On the nasa you can select the quicktime link to the right of the flash window.
Just install mplayer and it's firefox plugins. And it will stream it in the browser. Don't use totem plugin, remove if you have them.

---

### Post by Jagot on 2006-07-07
> **yopnono said:**
> On the nasa you can select the quicktime link to the right of the flash window.
Just install mplayer and it's firefox plugins. And it will stream it in the browser. Don't use totem plugin, remove if you have them.

The totem-xine-firefox-plugin is recommended by the Restricted Formats wiki and works fine for me.

---

### Post by tommcd on 2006-07-07
Thanks Jagot! I got the killsometime.com videos working! I installed:

gstreamer0.10-pitfdll
gxine
libxine-main1

from:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

That page seems to have been updated since I last checked it, or perhaps I missed a few things!
Do you know which codec, specifically is needed for killsometime.com? just curious?
I can't find the quicktime link at NASA, where is it? and thanks for the help!

---

### Post by yopnono on 2006-07-07
> **Jagot said:**
> The totem-xine-firefox-plugin is recommended by the Restricted Formats wiki and works fine for me.

Maybe so, But I still prefer mplayer and it's plugin, works better for me and on more places.

---

### Post by yopnono on 2006-07-07
> **tommcd said:**
> 
That page seems to have been updated since I last checked it, or perhaps I missed a few things!
Do you know which codec, specifically is needed for killsometime.com? just curious?
I can't find the quicktime link at NASA, where is it? and thanks for the help!

IE: Link: [http://www.jpl.nasa.gov/videos/mer/flightdir060630/](http://www.jpl.nasa.gov/videos/mer/flightdir060630/)
Look to the right of the flash window, see attached img

---

### Post by tommcd on 2006-07-07
Thanks yopnono! (feeling real stupid here!). I just thought that link was to install quicktime (ie, to install quicktime in windows!). 
Sometimes you just need a smack in the head, I guess! Thanks again!

---

### Post by cantormath on 2006-07-25
> **tommcd said:**
> I have pretty much every codec installed but when I try to watch videos here:
[http://www.jpl.nasa.gov/multimedia/](http://www.jpl.nasa.gov/multimedia/)
I get sound, but no video. They seem to use flash. I can watch most flash videos, but not at nasa. Also here:
[http://www.killsometime.com/Video/Videos.asp](http://www.killsometime.com/Video/Videos.asp)
again, sound but no video.
Can anybody watch these? and know what I need to watch them? Any help appreciated, thanks!


I remember when I couldnt see anything on the net. Use automatix.
[http://ubuntuforums.org/showthread.php?t=190025](http://ubuntuforums.org/showthread.php?t=190025)

just follow the tutorial on how to install automatix, and run automatix, Applications>System Tools>Automatix.
click the codecs, it will install it all correctly.


when its down, make sure you click ok to set the repositories back to the ones you had, it will ask you.

---

### Post by ashmew2 on 2007-02-15
Now not even flash 8 but flash player 9 has been develpoed for linux so long..!!
[www.adobe.com](www.adobe.com)

---

### Post by Ramses de Norre on 2007-02-15
Flash 9 is in the backports repo and the video's on NASA's site work fine with it.

---

