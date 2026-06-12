---
title: "Firefox 'send link' problem."
date: 2008-04-27
forum: General Help
---

### Post by RumorsOfWar on 2008-04-27
This is a weird problem. I tried to set the Firefox 'send link' function to point at a webmail link ( I can't find a pluging that works with FF 3). Now it doesn't work at all. How can I reset it to point at Thunderbird????

---

### Post by RumorsOfWar on 2008-04-27
I found info on using 'about:config' to set all preferences, [About:config]("http://http://kb.mozillazine.org/About:config_entries")
But even after entering' network.protocol-handler.app.mailto /usr/lib/thunderbird/thunderbird' no luck, so I reset all values to defaults. Still nada.
I'll just have to wait until a plugin gets updated to Firefox 3.

---

### Post by chandra on 2008-04-28
I am having a similar problem although I do not use a plugin. I am unable to click on mailto links in Firefox 3.0b5 and automatically open up a Thunderbird compose window, as used to happen with FF 2.0.0.n. I have filed a bug report at:

[https://bugs.launchpad.net/bugs/222944](https://bugs.launchpad.net/bugs/222944)

By the way, can you please explain the function that you are talking about. Is it an add-on, or is it a standard function?

Thanks.

Chandra

---

### Post by RumorsOfWar on 2008-04-28
> By the way, can you please explain the function that you are talking about. Is it an add-on, or is it a standard function?
The standard File function. The first time you use it, it *should* ask you what you want it to do, ('open default email client ? ..or somesuch).
 Firefox 3 is still beta, so I couldn't find any plugins to control that. Hopefully, that may be available soon.

---

