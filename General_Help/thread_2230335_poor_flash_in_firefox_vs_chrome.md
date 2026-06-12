---
title: "poor flash in firefox vs chrome?"
date: 2014-06-18
forum: General Help
---

### Post by princeofnam on 2014-06-18
I'd like to support firefox over chrome but I've been experiencing an annoying issue with flash and firefox.  In Chrome I can watch most videos at the highest resolution allowed by the video.  On Firefox for whatever reason these higher resolutions aren't offered.  Is anyone else having issues with this? I haven't had this issue on my Windows computer.

---

### Post by monkeybrain20122 on 2014-06-18
Which sites? I know on youtube the highest resolution (1080p) for html5 is only offered on Chrome, but for flash you can get the highest resolution on FF as well.
flash is more up to date in Chrome (but 11.2 works for most sites anyway). 

Flash and html5 are in general smoother in  Chrome because of hardware acceleration (as long as your gpu supports it or if you enable overriding software rendering in about:flags), so for machines with weak cpu Chrome performs a lot better on flash and html5 streams if gpu is good,  but then  Chrome doesn't support plugins so other things won't work.

You can have two browsers, it is not like you have to give up Firefox in order to use flash.

---

### Post by princeofnam on 2014-06-18
Right now i'm talking about youtube videos.  I use flash-aid to keep my flash up to date with firefox.. . is this a dated way to keep up to date?

---

### Post by monkeybrain20122 on 2014-06-18
flash-aid has been dead for more than 2 years and there is no more flash version updates for Linux since 2012 except through Chrome (system flash is stuck at 11.2 with only security updates, Chrome has the latest version 14). Which Ubuntu are you using and when was the last time you updated Firefox??

---

### Post by princeofnam on 2014-06-18
haha.  i've been using kubuntu 14.04  Firefox is v29 .  Usuaully update firefox with regular frequency as ubuntu software updater suggests

---

### Post by monkeybrain20122 on 2014-06-18
Then it is strange that you could still get flash-aid, as I think it was removed from the server long long time ago.

---

### Post by princeofnam on 2014-06-18
Laptop is +2yrs old unfortunately

---

### Post by monkeybrain20122 on 2014-06-18
2 years old laptop is new in my book. Mine is ~4 years, doesn't have any problem and performs great. :) But that has nothing to do with the non-availiability of flash-aid.

---

### Post by princeofnam on 2014-06-18
sorry. yea my laptop is otherwise fine.  i just mean i never bothered to remove the addon since i never knew the addon became obsolete.  anyway im just using a flash downloader to download the videos so that i can watch them on high res.  still not sure why firefox can't view in high res.

---

### Post by monkeybrain20122 on 2014-06-18
Get a link to such a site?

---

### Post by princeofnam on 2014-06-18
[https://www.youtube.com/watch?v=tV_lkWcjlsk](https://www.youtube.com/watch?v=tV_lkWcjlsk)

---

### Post by monkeybrain20122 on 2014-06-18
Well I got the highest resolution as 720p on both Chrome and Firefox. On Chrome it is in html5, on Firefox flash 11.2

---

### Post by princeofnam on 2014-06-18
hmm.  how'd you check the flash version on your firefox?

update: adobe's site confirmed "You have version 11,2,202,228 installed"

---

### Post by monkeybrain20122 on 2014-06-18
Right click the video, or go to Tools > Addons > Plugins

---

### Post by princeofnam on 2014-06-18
okay.  i figured out what was going on.  I disabled html5 on youtube.  Doing so I could watch the video in 720 but now It wont let me boost the speed.  lame trade off

---

### Post by monkeybrain20122 on 2014-06-18
Hmm... I am not sure what you are doing. 

On Firefox with flash you can watch Youtube at whatever resolution, but with html5 you cannot watch higher than 720p (or 480p for that matter since these resolutions use a format called 'dash' and it is only implemented in Chrome and the latest IE in Windows8, there is a ticket in Firefox's bugzilla to implement it) 

On Firefox the default is flash if you have it installed, otherwise it will fallback to html5, there may be some videos which are only in html5, but I don't know, so not sure why you would need to disable html5 or how you did it. On Chrome all videos are defaulted to html5 unless the html5 version doesn't exist and in that case it will fallback to flash, so it is the other way around.

Since I typically don't use flash on Youtube I haven't paid too much attention to these things so I may be missing something (I use a greasemonkey script called Viewtube to play these videos in mplayer, can't play dash format but my screen is 1366X768 so I don't really care that I can't watch 1080p this way)

---

### Post by princeofnam on 2014-06-18
you can easily switch back and forth using [http://www.youtube.com/html5](http://www.youtube.com/html5).  i enabled it because i wanted to watch videos in 2x speed.  unfortunately as we both know I can't watch videos past 320p. oh well it's okay. i'm just going to keep whati 'm doing and downloading the videos to enjoy the best of both worlds.  thanks for your help though

---

### Post by monkeybrain20122 on 2014-06-18
Glad that you find a solution that you are happy with, but still I don't understand why you have problem with flash for 720p+ on Firefox (for Youtube). As said I have no issue here.

---

### Post by princeofnam on 2014-06-18
so you have HTML5 enabled and can watch it at  720p and 2x speed?  hmm.  i wish i knew why i can't do the same

---

