---
title: "Firefox 30+ Adobe Flash alternatives?"
date: 2014-06-14
forum: General Help
---

### Post by temmokan on 2014-06-14
Hello,

OS: Ubuntu 12.04 x86_64.

Starting from Firefox 30, the Flash player I used so far (Shockwave Flash plugin, current version 11.2.202.378) starte dto crash almost on any page (PayPal, Google services etc). 

Could someone recommend alternatives for Firefox (switching to another browser is an awkward solution, I'd prefer to stay with Firefox). 

Thanks in advance.

---

### Post by caver12 on 2014-06-14
In snaptic look for gnash recommended or lightspark.

---

### Post by monkeybrain20122 on 2014-06-14
You flash profile may be corrupted. Open the file manager, press ctrl+h or show hidden file and then find and delete the hidden folder .adobe (note the "." in front)

If that doesn't work it may be becauseyou have hardware acceleration enabled. if so disable it (if you have created a file /etc/adobe/mms.cfg, delete/rename it. also right click on a video and then disable hardware acceleration)

> **caver12 said:**
> In snaptic look for gnash recommended or lightspark.

Do these ever work for you on any site other than the few (< 5) domo videos on Youtube? gnash and lightspark are complete waste of time and only clutter up your system, I wish people would stop recommending them (evidently without ever trying them out)

---

### Post by temmokan on 2014-06-15
> **monkeybrain20122 said:**
> You flash profile may be corrupted. Open the file manager, press ctrl+h or show hidden file and then find and delete the hidden folder .adobe (note the "." in front)

Tried to delete profiles for Firefox and Adobe. Doesn't help. Note: ~/.adobe wasn't updated for a long time, looks like Adobe Flush plugin 11.* doesn't sue it.

> **monkeybrain20122 said:**
> If that doesn't work it may be becauseyou have hardware acceleration enabled. if so disable it (if you have created a file /etc/adobe/mms.cfg, delete/rename it. also right click on a video and then disable hardware acceleration)

Hardware acceleration is on for two days only. Flush plugin started to crash Firefox only since Firefox 30, with and without hardware acceleration. Also, I see no sense installing GPU and disabling hardware acceleration.

Also, Google Chrome's bundled Flush player doesn't crash.

> **monkeybrain20122 said:**
> Do these ever work for you on any site other than the few (< 5) domo videos on Youtube? gnash and lightspark are complete waste of time and only clutter up your system, I wish people would stop recommending them (evidently without ever trying them out)

TWIMC, lightspark crashed Firefox in exactly the same manner on very same sites. I had bad experience with Gnash several ties, and this time I preferred to avoid it.

Thanks for your pieces of advice.

---

### Post by monkeybrain20122 on 2014-06-15
Can you test with a new Firefox profile? Close Firefox, rename ~/.mozilla to something else like ~/.mozilla-old then start Firefox and try again. To go back to the old profile, close Firefox, delete ~/.mozilla and rename ~/.mozilla-old back to ~/.mozilla.

Edited: Sorry, it seems that you did that already. BTW, gpu acceleration for flash only works on Youtube, so no big deal to disable it. There are other ways to watch Youtube without flash.

---

### Post by dragonfly41 on 2014-06-15
I read in one mozilla thread that Ebates Cash Back addon might be one cause of Firefox crashes.

Do you have this installed?

---

### Post by temmokan on 2014-06-16
[QUOTE=dragonfly41]I read in one mozilla thread that Ebates Cash Back addon might be one cause of Firefox crashes.

Do you have this installed?[/QUOTE]

No, I don't use that plugin.

[QUOTE=[COLOR=#000000]monkeybrain20122[/COLOR]][COLOR=#000000]Edited: Sorry, it seems that you did that already. BTW, gpu acceleration for flash only works on Youtube, so no big deal to disable it. There are other ways to watch Youtube without flash.[/COLOR][/QUOTE]

YouTube movies were never causing Flash /browser to crash. Now they do, and a lot of other sites using Flash, as well (e.g., PayPal). I think there's some incompatibility with the latest Firefox and Adobe Flash 11.

---

### Post by monkeybrain20122 on 2014-06-16
> **temmokan said:**
> No, I don't use that plugin.



YouTube movies were never causing Flash /browser to crash. Now they do, and a lot of other sites using Flash, as well (e.g., PayPal). I think there's some incompatibility with the latest Firefox and Adobe Flash 11.

No, it works fine here. Only Ted.com crashes on onr machine but that can be fixed by turning off hardware acceleration (I made a script to turn it on and off)

---

### Post by pickarooney on 2014-06-18
Firefox 30 just crashes constantly, on linux and Windows. If you can revert to 28 or wait until they fix the problem, do that. Nothing else is likely to sort it out.

---

