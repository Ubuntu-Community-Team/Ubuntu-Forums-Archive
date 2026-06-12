---
title: "browser-plugin-freshplayer-pepperflash doesn't work on Xubuntu 16.04"
date: 2016-06-25
forum: General Help
---

### Post by ardouronerous on 2016-06-25
[IMG]https://i.imgur.com/K15gwZQ.png[/IMG]

I've installed browser-plugin-freshplayer-pepperflash via Synaptic Package Manager, and the result is the image above, I have 11.2.202.626 installed, but my flash games barely runs on that, so I need to use 22.0.0.192.

I'd like to avoid installing Chromium, if I could.

---

### Post by ajgreeny on 2016-06-25
You must have the **adobe-flashplugin** package installed from the canonical-partners repos; it is the only way you will get flash version 22 in firefox, and also in midori, if that is of interest to you.

I am not sure why, but **browser-plugin-freshplayer-pepperflash** will work only if you have that and not if you installed flash with the **flashplugin-installer** package.  I have just this minute double checked that in my Xubuntu 16.04 virtual machine install where I had flash 22 working in FF and midori; changing from the adobe package to flashplugiin-installer gave me the same error as you saw.

---

### Post by ardouronerous on 2016-06-25
Thanks so much, that worked. :)

They should put a sticky on this one, so people with similar problems to mine can see it.

---

