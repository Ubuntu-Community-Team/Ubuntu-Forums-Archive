---
title: "Recent Netflix issues"
date: 2019-07-03
forum: General Help
---

### Post by yurx cherio on 2019-07-03
Monday night something happened and Netflix stopped working when run in Chrome. It plays for ~15 seconds and then freezes. I thought it was a Chrome issue so I disabled all extensions and eventually re-set it to defaults losing all saved cookies and various site data. Nothing seemed to help. I tried playing it in Firefox after enabling DRM support. To my surprise it exhibited the same symptoms. Tried with a blank browser profile, tried spoofing browser User agent without success, tried disabling plugins.

So I tried on 2 more Ubuntu workstations one 16.04 and another 18.04. Exact same issue!

So I thought this was a Netflix issue and asked people on Reddit and people with other Linux distributions (e.g. Arch & Devuan) don't experience this issue.

I noticed one of the recent updates brought changes to Ubuntu DRM libraries. This certainly could be the reason.

I am alone with this? Is anyone else experiencing Netflix playback issues? I welcome any suggestion on what I can do to fix this.

---

### Post by wildmanne39 on 2019-07-03
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by uRock on 2019-07-03
I am not having this issue in Chrome on Ubuntu 18.04.

---

### Post by yurx cherio on 2019-07-03
Did you update your system recently? I am thinking whether this was one of the latest updates causing this

---

### Post by deadflowr on 2019-07-04
> I noticed one of the recent updates brought changes to Ubuntu DRM libraries.
Different DRM.
The Ubuntu DRM updates were for graphic card related drm (direct rendering manager)
Netflix DRM is digital rights management, and those are part of the browser and not Ubuntu packaged anyway.
(The widevine DRM module is built into Chrome and is directly installed by Firefox
both are done outside Ubuntu packaging system)

Also, count me as one with normal playback.
Fully up-to-update.


Do you have other devices (non-linux) that can stream Netflix?
And do they stream fine?

And how are other streaming services playback?
Like youtube. (or any number of services out there)

---

### Post by yurx cherio on 2019-07-04
Other devices are Androids and Rokus stream Netflix well. Youtube, SlingTV, Amazon Prime Video - all stream well in Chrome and Firefox both on my 16.04 and 18.04 workstations.

The fact that I seem to be alone in this predicament makes me think my account is messed up but when I contacted Netflix today I was repeatedly told they don't want to deal with me because I stream from Linux :(

---

### Post by SeijiSensei on 2019-07-04
Have you tried lying about your browser with an add-on like User Agent Switcher?

[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher-revived/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher-revived/)

Also for Chrome.

That said, I have no problems with Netflix either using Firefox on Kubuntu 19.04 without manipulating my user-agent string.

---

### Post by rbmorse on 2019-07-04
Try clearing all the stored cookies relating to Netflix (there may be several) and see if that helps. 

I'm not having problems now, but in the past it's helped with similar issues. If you let Chrome automatically sign you in to Netflix with a remembered login/password refresh that, too, although it's a mystery to me why that should make any difference.

---

### Post by yurx cherio on 2019-07-04
I tried all of the above, spoofing user agent strings, clearing netflix application data in development tools and even resetting the whole chrome by clearing all sites data, disabling all extensions etc :cry:

Anyway thanks everyone for your help. Maybe it's an omen for me to spend less time watching

---

### Post by kurt18947 on 2019-07-04
> **yurx cherio said:**
> I tried all of the above, spoofing user agent strings, clearing netflix application data in development tools and even resetting the whole chrome by clearing all sites data, disabling all extensions etc :cry:

Anyway thanks everyone for your help. Maybe it's an omen for me to spend less time watching

I'm not a Netflix user but here's something that has helped me in the past with similar issues. Create another user and log in as that user. Try to stream Netflix. If that doesn't work either you've got something going on with your install. If it does work there may be something corrupt in your Ubuntu user account.

---

