---
title: "youtube &quot;video unavailable&quot; problem"
date: 2013-06-30
forum: General Help
---

### Post by kurja on 2013-06-30
Recently I started to get a "this video is currently unavailable" error in like every other youtube video, videos that I can view just fine on my android based mobile device but not on my ubuntu desktop, using either chromium or firefox. Any idea what might be wrong?

a random example: [http://www.youtube.com/watch?v=ej7dfPL7Kho](http://www.youtube.com/watch?v=ej7dfPL7Kho)

edit - I can also get the video with youtube-dl without any problem.

---

### Post by deadflowr on 2013-06-30
i just ran that link on firefox without any problems.

What version of flash do you have installed?

---

### Post by chemicalscum on 2013-07-01
> **kurja said:**
> Recently I started to get a "this video is currently unavailable" error in like every other youtube video, videos that I can view just fine on my android based mobile device but not on my ubuntu desktop, using either chromium or firefox. Any idea what might be wrong?

a random example: [http://www.youtube.com/watch?v=ej7dfPL7Kho](http://www.youtube.com/watch?v=ej7dfPL7Kho)

edit - I can also get the video with youtube-dl without any problem.

This is a problem created by Google playing up and apparently due to the politics of webM.  You are enrolled in the youtube HTML5 trial.  Google is no longer delivering HTML5 with H264 encoding to it's opensource Chrome, only HTML5 with its own opensource webM encoding.  I have this problem with Chromium and the problem is not present in Chrome when I installed it.  You are seeing the problem with Firefox as you presumably don't have flash installed.  If you had  Flash installed youtube would deliver you the Flash version.  However in Chromium it won't do that, however if you have flash and leave the HTML5 trial it will deliver everything in Flash.

You therefore have two options; install Flash and leave the HTML5 trial or install Chrome and use it instead (user agent spoofing Chrome in Chromium doesn't work).  Google is sort of shooting itself in the foot here but they must have their reasons.

Thanks for the video link I followed it and it is great.

---

### Post by kurja on 2013-07-07
Yay, I installed google chrome and it just works, thanks. Not going to fiddle with flash any more than absolutely necessary... that vile invention of Beelzebub, argh.

Lind & Micucci have some funny songs, happy to spread the good stuff =D

---

