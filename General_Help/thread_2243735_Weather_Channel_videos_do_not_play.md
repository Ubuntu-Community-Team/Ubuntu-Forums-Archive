---
title: "Weather Channel videos do not play"
date: 2014-09-10
forum: General Help
---

### Post by TheTinyt1 on 2014-09-10
I have 3 different flavors of Ubuntu on three different machines and all three have the same problem.

When I go to the weather channel web sit and try to watch the videos they have there none of my machines will play the videos any more. This just happened a few months ago. I took so long to search because I figured it was just a bug that was being worked on. But is has now on just a little too long. Please advise what I can do. 

YouTube videos play just fine as well as other web sites.

---

### Post by Frogs Hair on 2014-09-10
I see the same in Opera Developer with Pepper Flash and Firefox With Adobe Flash . If they were using Silverlight normally there would be a prompt to install , but that would be odd considering only about .2% of websites still use it. I'll see what happens on the Win 7 side with no Silverlight  and check back.

Edit: Opera and IE play videos  fine with the current Flash version in Windows with no Silverlight . I have the Ubuntu restricted extras installed and the video thumbnails are visible on the page but the embedded player never appears even with script blockers disabled. I am not prompted to install additional codecs either.

---

### Post by Frogs Hair on 2014-09-10
Update, I am getting playback of some video under the news tab using Flash , but not under the video tab. One video gave a Silverlight install prompt. It seems the site is using different players.

---

### Post by TheTinyt1 on 2014-09-11
I forgot to inform you that I am having this problem in Lubuntu with the native browser and Chrome and FireFox. I have uninstalled Firefox and Chrome with no improvement. I do not have a Ubuntu flavor running on anything to test that.

---

### Post by anika200 on 2014-09-11
> **TheTinyt1 said:**
>  try to watch the videos they have there none of my machines will play the videos any more. 

Do you have some links, that would be handy for us to check it out.

---

### Post by Habitual on 2014-09-11
weather.com/video/anything...
It's not specific to Ubunutu either. Someone reported success over at [http://forums.linuxmint.com/viewtopic.php?f=48&t=177327](http://forums.linuxmint.com/viewtopic.php?f=48&t=177327)

---

### Post by mc4man on 2014-09-11
> **Habitual said:**
> weather.com/video/anything...
It's not specific to Ubunutu either. Someone reported success over at [http://forums.linuxmint.com/viewtopic.php?f=48&t=177327](http://forums.linuxmint.com/viewtopic.php?f=48&t=177327)

That's what works here (setting user agent IE8 on weather channel, adblock+ doesn't matter

---

### Post by anika200 on 2014-09-11
Oh yeah, please disable all extensions and see if it works. That should be standard practice for all browser trouble shooting sessions.

---

### Post by Habitual on 2014-09-12
> **mc4man said:**
> That's what works here (setting user agent IE8 on weather channel, adblock+ doesn't matterI tied the IE8 UserAgent string and it did not work for me.

---

### Post by mc4man on 2014-09-17
> **Habitual said:**
> I tied the IE8 UserAgent string and it did not work for me.

Are you sure it's set? Here I change it, then open weather channel. Once FF is closed it goes back to orig. default for user-agent
(Edit - in screen 2 it's not yet set as the 'dot' is still on Default

---

### Post by Habitual on 2014-09-18
They play in Google Chrome Version 37.0.2062.120 (64-bit) with the default user agent string.

---

### Post by Mike_Walsh on 2014-09-18
I have to agree with Frogs Hair on this one; I think they MUST be using different players.

I'm dual-booting Ubuntu 14.04 & Zorin's OS Core 9 ( which is based on 14.04). They've both got Chrome and Firefox installed. Watching the Weather Channel on either browser, in either OS, seems to result in perfect playback on the /news videos; but trying any of them playing anything under the /video heading, for me at least, results in very choppy playback. Theses are fairly standard set-ups; I don't have much in the way of extensions apart from Ghostery and the appropriate flash players for each one.

Regards,

Mike.

Edit; possible reason for my particular results could be because I have an old, single-core Athlon 64; but under normal circumstances, it performs very well indeed...more than fast enough for my needs. Proves you don't need multi-core processors to play music, vids AND any couple of other apps at the same time; I don't even get any noticeable slowdown, which you would expect from an old CPU like that when trying to run multiple programs. Perhaps I've just got a good one...

---

### Post by Frogs Hair on 2014-09-18
Oddly enough all tested videos are playing today in FF 32 and I don't know the reason for change.

---

### Post by Mike_Walsh on 2014-09-18
Hm! The mysteries of modern technology.....

Regards,

Mike.


Edit; Upon re-watching the '/video' videos, even those now seem to be playing OK. Could be our broadband; it's a bit hit-and-miss at the best of times. Sometimes better than 40 Mb/s (good for the UK!), sometimes less than 5 Mb/s...

---

### Post by mc4man on 2014-09-18
Yeah - out of the blue WC vids now work without having to set a user agent. Guess they made some change or whatever.

---

### Post by TheTinyt1 on 2014-09-26
not sure what happened or exactly when, I tried to view a video the other day and it was working. Have tried quite a few of them and they are working fine now. 

Some one did something to the software in system upgrade evidently and every thing is work fine. Go figure...

---

