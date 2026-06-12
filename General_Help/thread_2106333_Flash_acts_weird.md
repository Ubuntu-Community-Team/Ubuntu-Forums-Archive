---
title: "Flash acts weird"
date: 2013-01-18
forum: General Help
---

### Post by devonmiles on 2013-01-18
Couple of weeks ago I did an update on my 11.10 after several months without update. Before everything was fine, but after the update Flash began not to work properly. Strangest is that certain Youtube videos play while some others don't but throw a message telling me that Adobe Flash Player is required. I use Chrome mainly, but it is the same in Opera too.
Any suggestions? Anybody else with similar issues?
Thanks in advance.

---

### Post by lisati on 2013-01-18
You might want to check out [flashaid]("https://github.com/webgapps/flashaid/wiki"), which can help resolve *some* issues with flash.

---

### Post by sdpagent on 2013-01-18
> **devonmiles said:**
> Couple of weeks ago I did an update on my 11.10 after several months without update. Before everything was fine, but after the update Flash began not to work properly. Strangest is that certain Youtube videos play while some others don't but throw a message telling me that Adobe Flash Player is required. I use Chrome mainly, but it is the same in Opera too.
Any suggestions? Anybody else with similar issues?
Thanks in advance.
Hmm. Were the videos that didn't play ones that you rented or paid for? In which case follow [this tutorial]("http://programster.blogspot.co.uk/2012/07/ubuntu-fix-not-being-able-to-stream.html").
Otherwise, perhaps you didn't actually have flash installed and the videos that did play were actually playing back in html5 not flash.

Programster

---

### Post by devonmiles on 2013-01-19
Thank you guys for the suggestions. It seems I didn't have Flash installed, probably that html5 thing confused me which I didn't know about. Now I have it installed and enabled as explained here: [http://helpx.adobe.com/flash-player/kb/enable-flash-player-google-chrome.html#main-pars_header_0](http://helpx.adobe.com/flash-player/kb/enable-flash-player-google-chrome.html#main-pars_header_0)
It has made a little difference: the message I get now is "Couldn't load Shockwave Flash". Google-ing it didn't help much.
Any further ideas?

---

### Post by efflandt on 2013-01-19
Are you running 32-bit or 64-bit Linux?  If you get the wrong bit flash it will not work natively.  And when you say Chrome, are you actually running Google Chome or chromium-browser?

The usual way to install flash in Ubuntu is to install **flashplugin-installer** (or **ubuntu-restricted-extras** which includes flash and a bunch of codecs).  That should automatically work for firefox, chromium browser, etc., but if you installed some other flash that does not work, you may need to remove that first.

Not sure about Google Chrome though, I tried running a version of that for a PC and it would run in virtualbox, but I could not get it to boot from USB stick on my Acer W500P tablet PC (which boots 64-bit Ubuntu and Lubuntu 12.04 from its internally USB connected SD card slot).

---

