---
title: "Flash player crashes"
date: 2014-07-04
forum: General Help
---

### Post by dexter14 on 2014-07-04
Apparently this happens to a ton of people? This is my first time ever using Linux and I have just installed and set up Lubuntu (I think the most recent version) and downloaded chrome. Checked out youtube, videos work fine. Went to twitch.tv, shockwave player crashes every time.

I've tried everything that I could find by researching it, but nothing has seemed to work. Anyone familiar with this problem know of a way to fix it? Any help is greatly appreciated, thanks!

Edit: Flash works fine in Firefox, although crashes on twitch.tv in chrome (not youtube). Something wrong with chrome perhaps?

---

### Post by claracc on 2014-07-04
I have last firefox 30.0 and adobe flash player 11.2.202.378 and there is not any problem with videos in twitch.tv, they play well without crashing adobe flash.

I think your problem is the browser chrome and adobe flash plugin working together, I would select in chrome to use the pepper flash plugin and disable the adobe flash one in the page  chrome://plugins/

---

### Post by dexter14 on 2014-07-04
> **claracc said:**
> I have last firefox 30.0 and adobe flash player 11.2.202.378 and there is not any problem with videos in twitch.tv, they play well without crashing adobe flash.

I think your problem is the browser chrome and adobe flash plugin working together, I would select in chrome to use the pepper flash plugin and disable the adobe flash one in the page  chrome://plugins/

Im not sure what you mean, the one (and only one) flash player I have is the pepper flash "/opt/google/chrome/PepperFlash/libpepflashplayer.so", thats from the chrome://plugins page and there is only one of them. version 14

---

### Post by deadflowr on 2014-07-04
> **dexter14 said:**
> Im not sure what you mean, the one (and only one) flash player I have is the pepper flash "/opt/google/chrome/PepperFlash/libpepflashplayer.so", thats from the chrome://plugins page and there is only one of them. version 14

That's how old chrome worked.
It could use both pepperflash, which is built into chrome, and flash installed on the system.
That stopped with chrome 34?, I think.

But it did not matter if you had both enabled, because chrome utilized the higher version unless that was disabled.
There was no conflict. Most people who have used (old)chrome have had both enabled and never even knew it.

The problem, unfortunately, is most likely the pepperflash plugin itself.
This is perhaps the best advice on reporting problems with it
[https://forums.adobe.com/thread/1073863?tstart=0](https://forums.adobe.com/thread/1073863?tstart=0)

---

### Post by dexter14 on 2014-07-04
> **deadflowr said:**
> That's how old chrome worked.
It could use both pepperflash, which is built into chrome, and flash installed on the system.
That stopped with chrome 34?, I think.

But it did not matter if you had both enabled, because chrome utilized the higher version unless that was disabled.
There was no conflict. Most people who have used (old)chrome have had both enabled and never even knew it.

The problem, unfortunately, is most likely the pepperflash plugin itself.
This is perhaps the best advice on reporting problems with it
[https://forums.adobe.com/thread/1073863?tstart=0](https://forums.adobe.com/thread/1073863?tstart=0)

Thanks for the great info, although its really sad and unfortunate. I love chrome (really dislike firefox). I guess for videos and the like i'm stuck with firefox for now. I'll be sure to file a report

Thanks again ):P

---

