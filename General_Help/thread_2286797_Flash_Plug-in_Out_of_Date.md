---
title: "Flash Plug-in Out of Date"
date: 2015-07-14
forum: General Help
---

### Post by GrouchyGaijin on 2015-07-14
Hi Guys,

Today I started getting notices in Firefox that it had prevented an outdated version of Adobe's Flash Plug-in from running.
When I go to the Adobe site I see that they have stopped issuing new versions of the plug-in for Linux.
[https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/)

[I]**NOTE**: Adobe Flash Player 11.2 will be the last version to target Linux as a supported platform. 
Adobe will continue to provide security backports to Flash Player 11.2 for Linux.

[/I]This reads to me as though the version currently in Ubuntu will receive security updates, but there will be no future versions.
According to Adobe's website the last Linux version of Flash Player is [B]Version 11.2.202.481

[/B]When I check Synaptic I see that I have **Version 1:20150708.1-0trusty1** which is listed as the latest version.
Are these, in fact, the same version, one with an Adobe version number and one with an Ubuntu version number?

What is everyone else using to watch Flash videos in Firefox if not Adobe Flash?

---

### Post by monkeybrain20122 on 2015-07-14
This is old news. Flash 11.2 works fine for most video sites. 

If up to date flash is needed there are a few solutions: use Chrome, running pepper-flash (up to date flash 18 from Chrome) in Firefox with a wrapper called freshplayer-plugin, use Windows flash with pipelight, and not use flash at all with the mpv addon (works for many sites though not all)

[http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)
[http://pipelight.net/cms/installation.html](http://pipelight.net/cms/installation.html)
[https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-us/firefox/addon/watch-with-mpv/)

Back in 2012 when adobe announced that it would stop updating flash on Linux there was quite a bit of panic but now it is pretty much a non issue because there are good workarounds and flash itself is dying fast.

---

### Post by GrouchyGaijin on 2015-07-14
I don't know about old news - the mainstream news sites I visit just started balking today when I tried to watch some videos.

---

### Post by monkeybrain20122 on 2015-07-14
> **GrouchyGaijin said:**
> I don't know about old news - the  mainstream news sites I visit just started balking today when I tried to  watch some videos.

Link?

BTW There is also some new news
[http://ubuntuforums.org/showthread.php?t=2286772](http://ubuntuforums.org/showthread.php?t=2286772)

---

### Post by Geoffrey_Arndt on 2015-07-14
Well, most of the top web video sites have moved, or are moving to html5 to replace flash . . . (apple was the start of the flash's demise).   The other alternative is to use pepperflash on the Chrome and/or Chromium browsers (which is updated thanks to Google's market influence).    Many folks say it's worth removing flash entirely, as it is one of the three most vulnerable apps on the web for exploits.

---

### Post by GrouchyGaijin on 2015-07-14
I guess I'll use Chrome for a while and hope that video at CNN et al. become available in Firefox soon

---

### Post by monkeybrain20122 on 2015-07-14
> **GrouchyGaijin said:**
> I guess I'll use Chrome for a while and hope that video at CNN et al. become available in Firefox soon

Flash not needed for CNN on firefox. The mpv addon works. See third link above

---

### Post by GrouchyGaijin on 2015-07-14
DOU!  I'm a goof.  It works so much better if mpv is actually installed.

This is cool.  Thank you.

---

