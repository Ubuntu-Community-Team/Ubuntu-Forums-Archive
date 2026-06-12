---
title: "Nvidia Soundstorm drivers with Firefox and Flash"
date: 2006-10-28
forum: General Help
---

### Post by joincamp on 2006-10-28
I followed a guide on here to get the nvsound drivers installed for my soundstorm chipset and it works well.  The problem is, is that it doesn't seem to work for anything that is ALSA.  So far this only seems to be a problem with firefox+flash.  i saw other posts about editing /etc/firefox/firefoxrc to include aoss, but that seems to be the opposite of what I want.

here is what shows in the term if i run firefox under it:

ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_hw.c:1355:(_snd_pcm_hw_open) Invalid value for card


please help, as this is quite annoying.

---

### Post by superami on 2007-01-22
If you haven't already found it, then you should check out this great post on the topic:

[http://www.ubuntuforums.org/showpost.php?p=1716845&postcount=61](http://www.ubuntuforums.org/showpost.php?p=1716845&postcount=61)

---

