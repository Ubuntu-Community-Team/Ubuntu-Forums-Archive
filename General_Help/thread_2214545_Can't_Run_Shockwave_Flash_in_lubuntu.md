---
title: "Can't Run Shockwave Flash in lubuntu"
date: 2014-04-01
forum: General Help
---

### Post by Mar Komus on 2014-04-01
Hello! First, thanks in advance for taking the time to read and consider :) This is a problem that's really driving me crazy. I resurrected an old computer of mine (my first build, really) to see just how far I can push the limits of Linux on slightly older hardware ;) I'm also testing different distros of Linux out-of-box to see which ones would be good for some clients who might be open to Linux in the wake of Microsoft's drop of Windows XP, but who might not be able to shell out for a whole new system. So far on this system (we'll call it, "x3m4") I've tested Ubuntu 13.10 (it failed because all I get is an orange or gray screen after log in) and Debian 7.4 (which also failed because of the current problem (no out-of-box playback of flash video; I've tried the html5 trick, too)).

So without too much further ado, here are x3m4's specs:

**Hardware specs:** ASUS A7N8X hosting AMD Athlon XP overclocked to 3200+ with 1GB DDR400 and NVIDIA GeForce FX 5500 (128 MB)
**OS:** lubuntu 13.10 32-bit

I've checked around other forums/discussions with people who have had a similar problem, so I'm documenting everything from scratch so we can start with a clean install. I'm starting this thread, then, with a clean install of lubuntu 13.10 without any updates (for testing purposes). I should point out that I also ran a live Debian 7.4 (i686 pae) DVD and successfully ran videos on YouTube via Iceweasel. ***Thus, we may safely eliminate hardware issues from the outset.*** 

Starting configuration: lubuntu 13.10 32-bit without updates
Testing apparatus: YouTube via firefox and chromium web browsers. 
Testing procedure: 1) open web browser 2) navigate to [www.youtube.com]("http://www.youtube.com") 3) attempt to play a video. Video plays = negative for bug. Video does not play = positive for bug.

*First Run: firefox*

Firefox version: 24.0 for Ubuntu canonical - 1.0
Shockwave Flash plugin: ver 11.2 r202 (updated behind my back during installation)

Test 1: application crash upon reaching [www.youtube.com;]("http://www.youtube.com;") no results
Test 2: video does not play. no crash. no warning signs.
Test 3: alternate method: navigate to adobe's shockwave flash test site. Says plugin is needed to display content.

Results: positive for bug

Adjust controls: update system (via root terminal using standard procedure: "apt-get update" and "apt-get upgrade")

Firefox version: 28.0 for Ubuntu canonical - 1.0
Shockwave Flash plugin: (same with only a slight variation in the fine numbers; failed to detail :mad: )

Test 1: same as Tests 2 and 3 above; no application crash

Results: positive for bug

*Second run: chromium (not installed by default; installed via Lubuntu Software Center and post updated system)*

Chromium version: 33.01750.152 Ubuntu 13.10 (256984)
Shockwave Flash plugin: (per directly above)

Test 1: Drop down warning: "Could not load Shockwave Fla..." Another drop down warning requesting permission to run
Test 2: (Click on a video link) Missing plugin graphic displayed in Flash field (where the video should play)

Results: positive for bug

**Conclusion:** This problem is not caused by hardware issues. It also arises regardless of which browser is used in these examples (noting the exception in Debian 7.4 i686 pae and Iceweasel).

So, since hardware is not the problem and videos will play only in Iceweasel--even though it doesn't have Shockwave Flash plugin (Why? I don't know. HTML5?), what's next? :)

**Summary:** Adobe's Shockwave Flash plugin works on the experimental system only under a live Debian 7.4 i686 pae session via Iceweasel--so far that I've tested. I've resisted going with just Debian because it runs too slowly on my system.

I'm open to suggestions: Install Iceweasel (apparently a complicated process)? Tweak firefox to do whatever it is Iceweasel does so it plays flash vids w/o flash player?

---

### Post by mörgæs on 2014-04-02
An Athlon XP does not have SSE2, which gives some problems for Flash. Have you tried installing Chrome? 

More info in the link in my signature.

---

