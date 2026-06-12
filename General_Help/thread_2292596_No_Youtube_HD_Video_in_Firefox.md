---
title: "No Youtube HD Video in Firefox"
date: 2015-08-29
forum: General Help
---

### Post by pearj2 on 2015-08-29
I'm running Lubuntu 15.04, and have restricted-extras, flash, etc installed - yet there is no HD video on Youtube in Firefox.

Any ideas?

(Note: 1080p videos work in Youtube using Chrome.)

---

### Post by monkeybrain20122 on 2015-08-29
Because since FF 40 it plays Youtube in html5 by default but Firefox cannot play html5 > 720p (only for Youtube because of Google's DASH format for video higher than 720p) It is on Mozilla's bugzilla, has nothing to do with Ubuntu. You can still watch 1080p and above if you use flash instead (there is a FF addon for always use flash on Youtube, don't remember what it is called) 

But since flash is bad in general I use the mpv addon [https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/](https://addons.mozilla.org/en-US/firefox/addon/watch-with-mpv/) (for this you need up to date mpv [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1) and youtube-dl [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)) In order to play 1080p and above go to Firefox > Tools > Addons > Extensions>  mpv  > Preferences > Additional Player Parameters add the line 
> --ytdl-format=bestvideo+bestaudio/best %u 

It works for many other sites with flash or html5 videos as well. One thing annoying about Youtube is that videos now autoplay if use html5 so either close the Youtube tab when mpv kicks in or use a FF plugin to stop HTML5 autoplay.

Edited: I use the parameter
> --ytdl-format=bestvideo[ext=mp4][width<=1920][height<=1080]+bestaudio[ext=m4a]/best[ext=mp4]/best %u
in mpv-addon, this way it doesn't play higher than 1920x1080p (machine can't handle) and always picks mp4 instead of webm so I can use hardware decoding. You may just need bestvideo+bestaudio/best

---

### Post by monkeybrain20122 on 2015-08-29
Ok. This Firefox addon both stops html5 videos from autoplaying and on Youtube if click allow will play video in flash (not sure if this is by desgin or a bug since it blocks both flash and html5 but the flash block ends up being displayed if both are present like Youtube, so clicking that will play video in flash ) [https://addons.mozilla.org/en-US/firefox/addon/flash-control/](https://addons.mozilla.org/en-US/firefox/addon/flash-control/)

---

### Post by pearj2 on 2015-08-29
I see.... as long as it's not Ubuntu and I can still watch HD via Chrome.

I'm going to be editing HD video (h264), and didn't want problems with it.

Seems like it'll be ok - thank you for your help!

---

### Post by monkeybrain20122 on 2015-08-29
You can still watch Youtube 1080p with Chrome on Ubuntu. It is a Firefox/Google issue and has nothing to do with Ubuntu and only affects Youtube.

---

### Post by Yellow Pasque on 2015-08-29
You may have to enable some special options to get greater than 720p on youtube (like mediasource extensions and fragmented-mp4):
[http://www.ghacks.net/2014/05/10/enable-media-source-extensions-firefox/](http://www.ghacks.net/2014/05/10/enable-media-source-extensions-firefox/)

---

### Post by mc4man on 2015-08-29
> **Temüjin said:**
> You may have to enable some special options to get greater than 720p on youtube (like mediasource extensions and fragmented-mp4):
[http://www.ghacks.net/2014/05/10/enable-media-source-extensions-firefox/](http://www.ghacks.net/2014/05/10/enable-media-source-extensions-firefox/)
I would think that is so - here FF plays youtube html5 @ 1080p fine. screens (- though I also use the mpv FF plugin instead of directly in browser.

---

### Post by Heeter on 2015-08-29
Hey

Just get the firefox addon "Youtube Flash HTML5"

---

### Post by monkeybrain20122 on 2015-08-30
I enabled media.mediasources.extension and it didn't do anything,still 720p max. Enabled media.mediasources.webm then the 1080p option appeared but Firefox crashes whenever I clicked it (was wondering why wasn't it enabled by default) I would just stick to mpv.

---

