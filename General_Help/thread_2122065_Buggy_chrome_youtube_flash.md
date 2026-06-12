---
title: "Buggy chrome youtube flash"
date: 2013-03-04
forum: General Help
---

### Post by yzuser on 2013-03-04
My system is running Ubuntu 12.04LTS and I'm getting buggy youtube flash videos with chrome. I don't get this with firefox, but when I watch youtube videos with google chrome, I get this pixel confetti effect on the video.  How do I fix this? See screenshot:


Note: not sure if this helps, but the pixel confetti move/regenerate when the video plays.  They pause in their places when I pause the video, HOWEVER, they move/generate when I move the mouse cursor into the video element, and they move/regenerate when I move the mouse cursor out of the video element.

[IMG]http://i.imgur.com/rR1iAfV.gif[/IMG]

---

### Post by yzuser on 2013-03-04
I stopped this effect by disabling the pepper flash plugin in chrome.  I'm not closing this thread because I don't understand why this stops the effect and because I don't see this as a real fix.

---

### Post by duke.tim on 2013-03-04
=========
yzuser Ninja Posted on me!
I'm guessing what you just did was disable the builtin flash from chrome
and are using the system flashplayer
=========
um Yikes! 
I'm not sure there is anything that you can do except wait for chrome to be updated. Which would be the safest/best bet.
I would suggest just using Firefox for flash.


If you absolutely want flash to work seamlessly on chrome this might work (or maybe not)
You might be able to force chrome to use a system flash version instead of the integrated version:


Download the Adobe Flash Player plugin here:
[http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect)
Copy the plugin here
```
[FONT=Arial]/opt/google/chrome/plugins/[/FONT]
```

Disable browser built in flash
Follow this guide:
[http://support.google.com/chrome/bin/answer.py?hl=en&answer=108086](http://support.google.com/chrome/bin/answer.py?hl=en&answer=108086)
or this one
[http://helpx.adobe.com/flash-player/kb/flash-player-google-chrome.html](http://helpx.adobe.com/flash-player/kb/flash-player-google-chrome.html)

---

### Post by vasa1 on 2013-03-04
> **yzuser said:**
> I stopped this effect by disabling the pepper flash plugin in chrome.  I'm not closing this thread because I don't understand why this stops the effect and because I don't see this as a real fix.
[http://askubuntu.com/questions/243313/why-is-google-chrome-displaying-artifacts-in-youtube/250534#250534](http://askubuntu.com/questions/243313/why-is-google-chrome-displaying-artifacts-in-youtube/250534#250534)

---

### Post by baillou2 on 2013-03-04
I'm having a worse problem where when I try watching a video I get full-on black and white static like on a tv and a message that says "this video currently unavailable", but if I go into Firefox it works just fine. 

This started about a week ago, and seems to affect mostly recent videos, but not older ones.

---

