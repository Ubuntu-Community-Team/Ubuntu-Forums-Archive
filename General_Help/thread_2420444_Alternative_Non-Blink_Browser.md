---
title: "Alternative Non-Blink Browser?"
date: 2019-06-05
forum: General Help
---

### Post by Daveski17 on 2019-06-05
I’ve been considering an alternative browser as a back up to Firefox. For a long time I used Chromium from the Ubuntu repo and eventually switched to Chrome. I like a back-up or alternative browser and usually have one at least. On macOS I have Safari and Firefox and neither of these have Blink as their rendering engine.

Unfortunately Google are going to phase out the webRequest API on Chromium which will affect all Blink engined browsers. The phasing out of webRequest API will basically make advanced adblocking impossible if I understand it correctly.

I’ve been considering several alternatives and have tried some WebKit based browsers from the Ubuntu repo. None of these seem to have workable adblockers though.

Pale Moon and SeaMonkey are contenders as neither employ Blink. Are there any problems or anything I should know about downloading and running either of these browsers on Ubuntu 16.04 LTS?

Thanks

---

### Post by #&amp;thj^% on 2019-06-05
As of today, you only have two viable choices for browser engines on most platforms: Firefox, with its** Gecko engine**, a_nd everything else, based on Blink._ Mac users have the option to use Safari as well, based on Webkit. That’s right, every other browser out there depends on Blink (most of the time being based on Chromium, the open source version of Chrome). Opera ? Ditched its own engine ages ago. Vivaldi ? Same. Brave browser ? Blink.
Microsoft has recently been the latest company to announce that their browser would put away its own engine to switch to Blink, the Google-driven fork of Webkit that powers Chrome, and, turns out, most of the available browsers these days. Edge used its own engine, and, while it worked all right, Microsoft decided that it just wasn’t getting the job done.
For myself Seamonkey is my go to browser.
To install: You need to execute the following commands to add repository, its key and package installation:
```

cat <<EOF | sudo tee /etc/apt/sources.list.d/mozilla.list
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
EOF

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2667CA5C
sudo apt-get update
sudo apt-get install seamonkey-mozilla-build
```

You will get SeaMonkey 2.49.4 with this method. And lots of stuff to tweak under the hood. (If you want)

---

### Post by Daveski17 on 2019-06-05
OK thanks. Is it possible to just download it from here?

[http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)

[ATTACH=CONFIG]283391[/ATTACH]

---

### Post by crip720 on 2019-06-05
Here is a list of different engines, but you will have study the browsers and see if any are suitable for what you want.  Netsurf looks interesting.   [https://en.wikipedia.org/wiki/Comparison_of_browser_engines](https://en.wikipedia.org/wiki/Comparison_of_browser_engines)  and different browsers  [https://en.wikipedia.org/wiki/Comparison_of_web_browsers](https://en.wikipedia.org/wiki/Comparison_of_web_browsers)

---

### Post by Daveski17 on 2019-06-06
> **crip720 said:**
> Here is a list of different engines, but you will have study the browsers and see if any are suitable for what you want.  Netsurf looks interesting.   [https://en.wikipedia.org/wiki/Comparison_of_browser_engines](https://en.wikipedia.org/wiki/Comparison_of_browser_engines)  and different browsers  [https://en.wikipedia.org/wiki/Comparison_of_web_browsers](https://en.wikipedia.org/wiki/Comparison_of_web_browsers)

Thanks, I've looked at a lot of these already. Although Netsurf is a new one on me. It doesn't appear to have an adblocker but I might have missed it when I was looking at the homepage. I honestly don't think there's a viable WebKit Linux browser available. Most seem to be abandonware. I reckon it will be down to Pale Moon or SeaMonkey. I have ran SeaMonkey on LXLE in the past, why it's not in the Ubuntu repo is a mystery to me lol.

---

### Post by nagfart203 on 2019-06-07
I usually used Safari and Firefox but since some time I have chosen Opera just because of Opera VPN plugin, as I need it in my profession. But of course, you can always choose another browser and use some VeePN service in order to hide your real IP address that is absolutely necessary for my job, for example.

---

### Post by Daveski17 on 2019-06-07
> **nagfart203 said:**
> I usually used Safari and Firefox but since some time I have chosen Opera just because of Opera VPN plugin, as I need it in my profession. But of course, you can always choose another browser and use some VeePN service in order to hide your real IP address that is absolutely necessary for my job, for example.

Opera is Blink engined though, It's not my IP address I want to hide. I want to hide from adverts.

---

### Post by kurt18947 on 2019-06-07
I've been using Vivaldi as a secondary browser but it depends on Chrome/Chromium so that doesn't help. I have some sites though where web form filling is required and Firefox doesn't work. I may have too many privacy add-ons in Firefox, dunno.

---

### Post by Daveski17 on 2019-06-07
> **kurt18947 said:**
> I've been using Vivaldi as a secondary browser but it depends on Chrome/Chromium so that doesn't help. I have some sites though where web form filling is required and Firefox doesn't work. I may have too many privacy add-ons in Firefox, dunno.

I ran Vivaldi four years ago on Ubuntu. Vivaldi say they're on top of this adblocking issue but I'm not so sure. 

[https://vivaldi.com/blog/chromium-ad-blockers-choice/](https://vivaldi.com/blog/chromium-ad-blockers-choice/)

---

### Post by #&amp;thj^% on 2019-06-07
> **Daveski17 said:**
> OK thanks. Is it possible to just download it from here?

[http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)

[ATTACH=CONFIG]283391[/ATTACH]

Yes but it won't automatically update. And I've never had a problem with the PPA for over 8 years now. ;)
It will take some getting aquatinted with it at first, but all kinds of modification's can be made under the hood or extensions. :D

---

### Post by Daveski17 on 2019-06-08
> **1fallen said:**
> Yes but it won't automatically update. And I've never had a problem with the PPA for over 8 years now. ;)
It will take some getting aquatinted with it at first, but all kinds of modification's can be made under the hood or extensions. :D

OK thanks. I ran SeaMonkey for years on Windows and I've run it on Linux.

---

