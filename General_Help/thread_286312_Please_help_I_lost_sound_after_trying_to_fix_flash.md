---
title: "Please help I lost sound after trying to fix flash sound problem"
date: 2006-10-27
forum: General Help
---

### Post by jdlite on 2006-10-27
I was attempting to fix the issue of having no sound with flash related apps like google video. I attempted this fix

[http://www.macewan.org/2006/06/01/ho...-linux-dapper/](http://www.macewan.org/2006/06/01/ho...-linux-dapper/)

and now I have lost sound to everything. Bootup, xmms, vlc player, etc. I have a line input from my dish network and it works so I know the card is installed working. This appears to be a config issue. Can someone please help

jaydee

---

### Post by DaveBorealis on 2006-10-27
Hello jaydee,
Your link doesn't go where I think you wanted it to go!
Dave

---

### Post by jdlite on 2006-10-27
[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/](http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/)

---

### Post by jdlite on 2006-10-27
Link should work now

---

### Post by jdlite on 2006-10-27
This is the fix i tried and lost sound to my whole system

Howto fix Firefox Flash Video Sound on Ubuntu Linux Dapper

If after a system update you’ve discovered that streaming Flash is without sound - fear not. Dapper will at times drop the sound from Firefox & Flash, as always you need to search the forums before freaking out as someone has more than likely already experienced the problem and discovered a solution. Trial and error has lead me to the following fix on my system.

sudo aptitude install alsa-oss
sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=”aoss”

---

