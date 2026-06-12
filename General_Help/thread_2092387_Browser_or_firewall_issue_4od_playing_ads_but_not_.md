---
title: "Browser or firewall issue? 4od playing ads but not programmes - possible ad-blocking?"
date: 2012-12-07
forum: General Help
---

### Post by ruthi13 on 2012-12-07
Hey, I'm stilll fairly new to Ubuntu (12.10) and the terminal in general so please be patient with me! Loving it though and am getting there (slowly). I don't have the dual-boot option so can't compare anything to Windows OS.

I have both Google Chrome and Firefox, and the problem occurs with both browsers. When I play 4od online, the ads all play fine, but the programme then does not load and I get a blank black screen. This happens with all 4od programmes in all the browsers I've tried 
(Opera and Chromium, even IE (!!) through Wine too) Under each browser's settings, adblock is off or there's no option for it, so wonder whether it's a bigger firewall-y type issue but can't see the obvious in OS settings. Can anyone help with terminal commands to figure out what's going on?

Thanks :)

Ruth.

---

### Post by zebb on 2012-12-12
Hi ruthi

can't offer a fix for your problem (I have the same issue) but this may help as an alternative:

[http://www.armedpineapple.co.uk/2012/09/downloading-programmes-from-4od-linux/](http://www.armedpineapple.co.uk/2012/09/downloading-programmes-from-4od-linux/)

---

### Post by Cheesemill on 2012-12-13
I have the same issue, it started about 4 months ago

I never bothered looking for a fix though because all of the content is also availible on the official 4od channel on YouTube.
[http://www.youtube.com/user/4od](http://www.youtube.com/user/4od)

---

### Post by lightning slinger on 2012-12-13
Try installing hal

sudo apt-get install hal

Streaming 4od works for me  in FF 17.0.1 in xubuntu 12.04

---

### Post by nicknamewinder on 2013-01-19
I had this same problem on ubuntu 12.10, with the add blocker turned off etc.  I found that the previous post worked for me.

sudo apt-get install hal

---

