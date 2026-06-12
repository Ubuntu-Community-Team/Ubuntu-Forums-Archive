---
title: "Watching Movies - Flash Player"
date: 2020-04-09
forum: General Help
---

### Post by stefankovac2266 on 2020-04-09
Hi. I have read that Google Chrome will not support Flash Player anymore after December 2020.
The question is: how will be I able to watch movies when Mozilla Firefox already can't play them and Google Chrome will also not support Flash Player in the future?

---

### Post by Holger_Gehrke on 2020-04-09
Firefox can play Flash if the plugin is installed;  it's almost the only plugin using the old Netscape Plugin API that Firefox still allows. To set it up install the package flashplugin-installer (sudo apt install flashplugin-installer). This package automates the process of installing flash and gets updated whenever there's an update for flash. But both browser will drop Flash at the date you quote because Adobe will stop all support for Flash at that point. Most major and a lot of the minor video sites have already stopped using Flash for video, they use the html5 video-tag in combination with lots of JavaScript for the user interface for controlling playback. If some site still uses flash it's either a site that has not been updated in a long time or it's in the process of setting up for the time after flash.

Holger

---

### Post by stefankovac2266 on 2020-04-09
Thank you very very much. It is working now also in Mozilla Firefox. Hopefully the websites where I use to watch movies will work in the future without Flash Player.

---

### Post by CelticWarrior on 2020-04-09
Sites that still use Flash for video are already dead since a long time ago but may not be aware of that (like some users) but in less than one year all of them will be very aware of that fact.

---

### Post by Frogs Hair on 2020-04-09
Adobe ends distribution and support for flash on  December 31, 2020.

---

### Post by sdsurfer on 2020-04-09
> Hopefully the websites where I use to watch movies will work in the future without Flash Player.

To directly answer the question (sorry if it's here and I overlooked it) modern web sites now use an html5 doctype which has access to the <video> element to deploy video, rendering Flash unnecessary. To test if your sites work, disable flash and go to the site. If the video does not play, it's on the developers of the site to update how they deploy video.

---

### Post by ajgreeny on 2020-04-09
If it's of any consequence to you, I haven't had flash of any sort on my computers now for a long time and have not noticed any difference to my browsing; videos still play when they are meant to using html5 as explained above.

---

### Post by VMC on 2020-04-09
You just need the proper codecs, not flash.

---

### Post by dragonfly41 on 2020-04-09
Keep tracking [HaXE]("https://www.flowplay.com/press-releases-posts/2017/12/12/flowplay-completes-major-cross-platform-overhaul-transitions-14-million-lines-of-code-to-haxe-for-vegas-world-relaunch").

---

### Post by stefankovac2266 on 2020-04-09
Thank you very much for the answers.

---

