---
title: "Adobe Flash Plugin and Fire Fox"
date: 2015-07-15
forum: General Help
---

### Post by lyni on 2015-07-15
hi
today as I've been going to various websites I've been getting a notice across the top saying 'Firefox Has Prevented The Unsafe Plugin Adobe Flash From Running On...' it then mentions the website. 

I checked on the Adobe website and it says 'Adobe Flash 11.2 will be the last version to target Linux as a supported platform. Adobe will continue to provide security backports to Flash Player 11.2 for Linux.'

does this mean that we can no longer use Adobe Flash plugin any more? and if that's the case what is the alternative?

I have Ubuntu 14.04

thanks for any assistance.
lyn

thanks everyone for your assistance. today Saturday 18 July I'm able to see youtube again.

---

### Post by monkeybrain20122 on 2015-07-15
Not the version, just that they have found another hole in flash
[http://www.zdnet.com/article/firefox-now-blocks-all-versions-of-flash-player-by-default/](http://www.zdnet.com/article/firefox-now-blocks-all-versions-of-flash-player-by-default/)

More here

[http://ubuntuforums.org/showthread.php?t=2285878](http://ubuntuforums.org/showthread.php?t=2285878)

---

### Post by lyni on 2015-07-15
> **monkeybrain20122 said:**
> Not the version, just that they have found another hole in flash
[http://www.zdnet.com/article/firefox-now-blocks-all-versions-of-flash-player-by-default/](http://www.zdnet.com/article/firefox-now-blocks-all-versions-of-flash-player-by-default/)

More here

[http://ubuntuforums.org/showthread.php?t=2285878](http://ubuntuforums.org/showthread.php?t=2285878)

hi Monkey I've just replied to you on another thread re the flash player. you had a link to mpv. is that easy to install on Ubuntu and will that work for youtube and other sites that need a flash player?
thanks
lyn

---

### Post by monkeybrain20122 on 2015-07-15
> **lyni said:**
> hi Monkey I've just replied to you on another thread re the flash player. you had a link to mpv. is that easy to install on Ubuntu and will that work for youtube and other sites that need a flash player?
thanks
lyn

It is supposed to work on all these sites.[https://rg3.github.io/youtube-dl/supportedsites.html](https://rg3.github.io/youtube-dl/supportedsites.html)
But obviously I haven't tested most of them, but I found that it works even on some sites not listed here (e.g the Guardian newspaper and some random sites with embedded flash videos)

You need to install up to date mpv and youtube-dl on your system to use the addon

youtube-dl is in the repo, but it is not up to date, you need to install from a ppa, google "youtube-dl Ubuntu ppa" (the moderator is not happy that I give the link. ;))

mpv from [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) (trusty) or [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1) (vivid)

---

### Post by lyni on 2015-07-15
> **monkeybrain20122 said:**
> It is supposed to work on all these sites.[https://rg3.github.io/youtube-dl/supportedsites.html](https://rg3.github.io/youtube-dl/supportedsites.html)
But obviously I haven't tested most of them, but I found that it works even on some sites not listed here (e.g the Guardian newspaper)

You need to install up to date mpv and youtube-dl on your system.

youtube-dl is in the repo, but it is not up to date, you need to install from a ppa, google "youtube-dl Ubuntu ppa" (the moderator is not happy that I give the link. ;))

mpv from [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media) (trusty) or [https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1](https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-test1) (vivid)

thanks monkey. its all too hard for me. I might have to wait until something more simple comes along that I can install from the Software Centre. or if Firefox brings something out for Ubuntu.
lyn

---

### Post by mastablasta on 2015-07-15
really complicated.... you open software center, go to software sources and add the PPA link to the sources. you update and then program mpv will appear in your software center. click install button. same for the other one

---

### Post by mc4man on 2015-07-15
> **monkeybrain20122 said:**
> 
You need to install up to date mpv and youtube-dl on your system to use the addon

youtube-dl is in the repo, but it is not up to date, you need to install from a ppa, google "youtube-dl Ubuntu ppa" (the moderator is not happy that I give the link. ;))

Here I just use ytdl from site & update weekly or so (sudo youtube-dl -U
Never saw that plugin before, seems to work ok - at first was visible with all those other little icons in top right area, now just in the 3 bar menu (I've no clue how you add to those always visible icons.

(mpv defaults to 720p (formerly best video/audio in ytdl) those wishing otherwise can fool with various options, either in mpv.conf or specific to the plugin (in .conf no -
1 ex. shown in screen, several variations, judicious use advised.. also note that duration is not available with such Dash options yet in mpv
(- 2nd. ex. ytdl-format=bestvideo+bestaudio/best

---

### Post by monkeybrain20122 on 2015-07-15
> **mc4man said:**
> Here I just use ytdl from site & update weekly or so (sudo youtube-dl -U
Never saw that plugin before, seems to work ok - at first was visible with all those other little icons in top right area, now just in the 3 bar menu (I've no clue how you add to those always visible icons.

I don't know, it is always visible here. Maybe you have too many icons on the tool bar (?) already?

> (mpv defaults to 720p (formerly best video/audio in ytdl) those wishing otherwise can fool with various options, either in mpv.conf or specific to the plugin (in .conf no -
1 ex. shown in screen, several variations, judicious use advised.. also note that duration is not available with such Dash options yet in mpv
(- 2nd. ex. ytdl-format=bestvideo+bestaudio/best


I set it in the addon's preference like --ytdl-format=137+141/137+140/best, bestvideo+bestaudio sometimes results in 1080p webm instead of 1080p mp4 for which hardware decoding does not work and I get green screen on intel  (mpv' issue you have commented on **Edited**: this was fixed in the latest mpv master)

Sure you can update youtube-dl manually but OP may prefer doing it with other updates with ppa, anyway, it is not kosher to give the link. :)

---

### Post by efflandt on 2015-07-15
If all else fails, Google Chrome includes its own pepper flash and can also do Netflix which does not work natively in Linux Firefox. Although, I think for for Netflix you may need to set your profile on Netflix website to "Prefer HTML5".

Not sure what the difference is between Chromium in Ubuntu repos or Chrome browser from Google itself, but I used Google Chrome with Chromecast Extension for a Chromecast device.

---

### Post by monkeybrain20122 on 2015-07-15
> **efflandt said:**
>  Although, I think for for Netflix you may need to set your profile on Netflix website to "Prefer HTML5".



No need to set preference on Linux because the alternative (silverlight) doesn't work. :)

---

