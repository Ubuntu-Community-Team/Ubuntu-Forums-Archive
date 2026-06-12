---
title: "Slow scrolling with Google Chrome and Synaptics touchpad"
date: 2016-07-10
forum: General Help
---

### Post by Maximus559 on 2016-07-10
I'm using Xubuntu 16.04 and Chrome 51 on two different notebooks, and I'm having the same problem on both. When I scroll using the touchpad, Chrome exhibits "smooth scrolling" behavior. This is a nice feature in theory, except that it causes quite a bit of lag - "jank" in browser terms. Overall responsiveness is reduced, and pages continue to scroll (slowly) after I take my finger off the touchpad. This is most pronounced on my Atom-based netbook, but it's noticeable on my Core i5 daily driver as well. I have smooth scrolling disabled in chrome://flags, so I'm guessing the smoothing is being done at the driver level. If I use a USB mouse or grab the scroll bar manually, this problem goes away.

I'm not sure if it's Chrome or the Synaptics driver that's causing the performance problems. I'm not crazy about smooth scrolling, so I wouldn't mind disabling it at the driver level if necessary. I've already disabled inertial scrolling, but can't find a way to disable smooth scrolling entirely.

---

### Post by xubu2 on 2016-07-10
Oops, wasn't paying attention.

Maybe this speeds things up:
[https://chrome.google.com/webstore/detail/smoothscroll/nbokbjkabcmbfdlbddjidfmibcpneigj](https://chrome.google.com/webstore/detail/smoothscroll/nbokbjkabcmbfdlbddjidfmibcpneigj)

I use this one for faster scroll speed with my mouse wheel:
[https://chrome.google.com/webstore/detail/chromium-wheel-smooth-scr/khpcanbeojalbkpgpmjpdkjnkfcgfkhb?hl=en](https://chrome.google.com/webstore/detail/chromium-wheel-smooth-scr/khpcanbeojalbkpgpmjpdkjnkfcgfkhb?hl=en)
But i don't know if it supports touchpads.

Cheers.

---

### Post by Maximus559 on 2016-07-28
This has been fixed in Chrome 52. The smooth scrolling flag in chrome://flags now works as expected.

---

### Post by alonsougc on 2016-12-02
> **Maximus559 said:**
> This has been fixed in Chrome 52. The smooth scrolling flag in chrome://flags now works as expected.

No...ithasnt'WHatiswrongwiththiswebsite??IcantUseTheSpaceKey...ButItWorksInAnyOtherWebsiteOrProgram...

---

### Post by Maximus559 on 2017-01-09
This problem is back as of Chrome 55. The smooth scrolling flag in chrome://flags again has no effect. I tried the --disable-smooth-scrolling mentioned [here]("https://github.com/mattermost/desktop/issues/388") but saw no change.

---

### Post by chris354 on 2017-01-10
I too have this issue in chromium (laptop can no longer install GC as they took the 32bit support away some time back). As chrome is/was heavily based on chromium I believe this is the same issue and I had considered it might be a driver issue but it does only seem to crop up on pages where there is a lot of javascript polling involved, its most prominent on me for websites like Facebook which has a vast number of scripts running to bring notifications, poll for more posts etc etc.

You can rule that out by disabling javascript for the website temporarily but im not too sure on how well you would be able to test on sites that rely on it to function, ive pretty much resigned myself at this point to a little lag in the scrolling.


> **alonsougc said:**
> No...ithasnt'WHatiswrongwiththiswebsite??IcantUseTheSpaceKey...ButItWorksInAnyOtherWebsiteOrProgram...

I found this earlier when replying with quote, but this time its corrected as you can see with this reply. Its possible that there are scripts not fully loaded by the browser, maybe waiting a while for full loading to complete will solve your space bar issue.

---

