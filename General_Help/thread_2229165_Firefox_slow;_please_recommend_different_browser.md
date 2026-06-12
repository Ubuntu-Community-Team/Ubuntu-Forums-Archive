---
title: "Firefox slow; please recommend different browser"
date: 2014-06-11
forum: General Help
---

### Post by Ralph L on 2014-06-11
I have been running Firefox for years, but recently I have noticed that it is becoming a cpu hog.  I often have many tabs open in multiple windows (one for each project, maybe 8 tabs in each).  Response gets slow.  When I watch System Monitor I see that my cpu usage is constantly pegged at, or near 100%.  My real memory is seldom full and I see only a small amount of swap space used.  Hence, I think my problem is too slow a cpu, not too small a memory.  I am running on an old Dell Latitude D610 with a single 2.13GHz processor (the fastest available for this computer).

Can anybody recommend a different browser that would have all the features of Firefox.  I am running the Adblock Plus, Better Privacy, UnMHT, PrintPdf, SavewithURL, and UnPlug so I would like those features in the new browser.  And I really like Firefox's ability to recover from system hangs, where I have to restart the computer, without loss of any windows.  I have been considering Opera and would appreciate any good or bad comments about it running  on Ubuntu 12.04.  Also, if anybody knows how I can make Firefox run faster, that would also be an alternative.

Thanks

---

### Post by ajgreeny on 2014-06-11
I am not too surprised that with those specs your machine is running slowly, particularly if some of those FF instances with one or more tabs have flash animations, as flash in Linux is a real resource hog.

If that is the main problem you may be able to avoid such a slow-down by adding the [**flashblock**]("https://addons.mozilla.org/en-US/firefox/addon/flashblock/?src=ss") add-on, or maybe no-script, though I find the latter a bit too much of a nuisance as it stops so many activities in FF that it becomes tedious to use, particularly if you are often going to new web-sites.

---

### Post by monkeybrain20122 on 2014-06-11
> **ajgreeny said:**
> I am not too surprised that with those specs your machine is running slowly, particularly if some of those FF instances with one or more tabs have flash animations, as flash in Linux is a real resource hog.

If that is the main problem you may be able to avoid such a slow-down by adding the [**flashblock**]("https://addons.mozilla.org/en-US/firefox/addon/flashblock/?src=ss") add-on, or maybe no-script, though I find the latter a bit too much of a nuisance as it stops so many activities in FF that it becomes tedious to use, particularly if you are often going to new web-sites.

You don't need flashblock. Just go to Tools > Addons > Plugins and  set flash to "Ask to activate", this option has been around for quite  some times so flashblock is no longer needed

I agree that flash is most likely the culprit too. I installed xubuntu on a machine with 1G of ram and a single 1.8GHZ processor, FF 29 handles 30+ open tabs easily and quite smooth. Only thing is, I pretty much block flash most of the time and I use Viewtube instead of flash for supported video streaming sites.[http://isebaro.com/viewtube/?ln=en](http://isebaro.com/viewtube/?ln=en)

FF 30 makes all plugins load on demand EXCEPT flash, that is quite dumb.

---

### Post by Ralph L on 2014-06-11
Thank you very much for the input.  I set Flash to "Ask to Activate", and ran Speakeasy, which requires Flash.  It asked me to activate Flash and had an option to set Speakeasy so that it always loaded Flash.  Without Speakeasy running my cpu usage was around 50%.  With Speakeasy running cpu usage went close to 100%.  So you guys hit the nail on the head.  Thank you.

I also wanted to load Viewtube, which is javascript.  Can you give me instructions for doing that?  Does it run as a stand alone application, or under Firefox?  When I went to the web site and clicked on what I thought was the download arrow, it took me to listing site.  I don't know how to download and install it.

Also, with Flash set to "Ask to Active" I found other sites that want Flash.  The latest one was United Airlines.  Is there any substitute for Flash that can be used on a site like United Airlines, or do I just have to activate Flash

---

### Post by monkeybrain20122 on 2014-06-11
For viewtube, first you need to install the greasemonkey addon for firefox. [https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/)
Restart Firefox, then go to Viewtube's site, click the blue arrow to install, that's it.

To use it you need to have either Totem or the mplayer plugin. Go to Tools > Addons > Plugins to check if either is installed already (the Totem plugins have descriptions like "compatible: videos") if neither is installed then just get gecko-mediaplayer or totem-plugins from the repo. Now go to Youtube, e,g you would be able to play the video without flash. You may want to set these plugins to 'Always activate' as they are set to 'Ask to activate' in Firefox 30, even though the only one plugin that should be set to 'Ask to activate' is not (flash) :)

Unfortunately there are still sites you need to use flash (like airline) but if you don't load it automatically and only use it when needed it should be ok. Also, you may want to try Chrome when you need flash, I find it a bit more efficient with things like flash and html5 (e.g vimeo) But Chrome doesn't handle many open tabs very well, so be warned. :)

---

