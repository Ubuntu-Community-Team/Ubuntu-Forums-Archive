---
title: "Firefox 3 or Hardy?  Screen goes B&amp;W, unresponsive"
date: 2008-04-25
forum: General Help
---

### Post by mhenry35 on 2008-04-25
I installed the Beta version of Hardy when it was released and have applied all updates, I check regularly to ensure I've got them all.

The system has worked very well for me, even the beta without any updates was great, this was the first time I've installed Linux without making any text based modifications and everything works!

Anyway, the only issue I have is that Firefox keeps going unresponsive (you can't even right click to get a menu) and then suddenly the screen goes black & white, then it goes back to color and the system responds again.  It was happening often enough that I started system monitor so I could see if the processor was overutilized, but when the screen went B&W and I switched to monitor, the CPU was not under heavy load, nor was there a high level of network activity, HD access, nothing, it was just normal system operations.  When the screen goes B&W, I'm sure it's intentional, to denote the system is busy (the transition is like theatre dimming, a controlled change.)

Last night, I didn't have firefox open, and the screen went black & white.  It's only happened once when Firefox isn't open, but I didn't check processes to see if there was a Firefox process hung up from my last session.

I'm thinking of removing Firefox 3 and reinstalling Firefox 2, but I wanted to run this past the forum to see if anybody else had this issue.

---

### Post by noynac on 2008-04-25
Firefox 3 can cause a lot CPU and hard drive activity when fetching updates to the site-forgery and malware lists contained in the file, urlclassifier3.sqlite. A temporary workaround (too see if this is causing your issue) is to uncheck the following Firefox security preferences:

* Tell me if the site I'm visiting is a suspected attack site

* Tell me if the site I'm visiting is a suspected forgery

A now-closed thread in the old Hardy forum provides more information on this issue:

[http://ubuntuforums.org/showthread.php?t=759673](http://ubuntuforums.org/showthread.php?t=759673)

---

### Post by anywebloco on 2008-04-25
I'm having this problem too. No excessive load to speak of.

---

