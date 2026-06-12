---
title: "Firefox youtube htnl5 player audio just noise"
date: 2015-09-23
forum: General Help
---

### Post by monkeybrain20122 on 2015-09-23
This happens with some Youtube videos using html5 player in Firefox. The videos play the audio is one long "wuuuuu" . Audio works with the mpv addon and on Chrome
For examples.

[https://www.youtube.com/watch?v=xEdpSgz8KU4](https://www.youtube.com/watch?v=xEdpSgz8KU4)
[https://www.youtube.com/watch?v=3ky_f_Y_bEU](https://www.youtube.com/watch?v=3ky_f_Y_bEU)


Firefox 41 on Ubuntu 15.04 ( I think it happened on FF 40 as well but I thought it was the video's problem)

Edited: don't know what happens with flash, apparently can't switch to flash any more.

---

### Post by monkeybrain20122 on 2015-09-23
Not only Youtube, happens on other html5 videos as well. e.g [https://vimeo.com/channels/staffpicks/140022562](https://vimeo.com/channels/staffpicks/140022562)
Some videos just show green with the strange sound.

---

### Post by d-cosner on 2015-09-23
This will allow you to switch between flash and HTML5.

[http://mybrowseraddon.com/youtube-flash-html.html](http://mybrowseraddon.com/youtube-flash-html.html)

The videos you linked to played fine for me. What graphics card are you using?

Edit: Here is the extension should you decide to give it a try.

[https://addons.mozilla.org/en-us/firefox/addon/youtube-flash-html5/?src=cb-dl-mostpopular](https://addons.mozilla.org/en-us/firefox/addon/youtube-flash-html5/?src=cb-dl-mostpopular)

---

### Post by Vladlenin5000 on 2015-09-23
Both YT and Vimeo videos posted above plays fine in my FF 43.0a2 (Dev.) with HTML5 on 15.04.

---

### Post by mikodo on 2015-09-23
I'm fed up with all the "dancing around" we do, to try to use HTML5 instead of flash with FF.

FF .v41 broke sound for me in YT too.

I have installed as extensions below ... and am going to "flush" them all. When HTML5 works better without all the extensions maybe, I'll try it again.

I'm going back to smtube or mpv. 

Deleting:

HTML5 Everywhere
NoFlash
YouTube Flash-HTML5

I really like the FF support you folks offer. Names that come to mind quickly are:

lovinglinux ...      where is he these days?
vasa1 ...              I have learned lots
monkeybrain ... I forget your numbers lol

Playing this stuff is not important to me anyway. I seldom watch it.

I'm just happy to have Adobe Flash and MS Silverlight  gone from my machine.

venting done

---

### Post by monkeybrain20122 on 2015-09-23
I have figured it out. I have enabled in about:config media.fragmented-mp4-use-blank-decoder accidentally while enabling the other ones. Setting it to default (false) fixed the problem.

Thanks for everyone who has taken an interest.

---

### Post by mikodo on 2015-09-24
> **monkeybrain20122 said:**
> I have figured it out.

Me too. I turned off my speakers last nite. I've done that no more than 5 times in the last 5 years. I noticed when I had no audio with Audacious. :redface:

Got the FF update, saw the thread, and jumped to conclusions.

HTML5 is working on YT fine. (I tried with the extensions again).

---

