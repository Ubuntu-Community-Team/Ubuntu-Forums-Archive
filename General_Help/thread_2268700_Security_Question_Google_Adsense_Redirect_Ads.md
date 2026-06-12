---
title: "Security Question: Google Adsense Redirect Ads"
date: 2015-03-10
forum: General Help
---

### Post by Nick_W on 2015-03-10
Hi,

I've been visiting summitpost.org (a forum/community on mountain climbing, using Ubuntu 12.04 and Chrome) and noticed that occasionally annoying ads have occured, some of which play sound and some of which are "hidden" hover ads which can redirect to another site when you hover the mouse over them. 

I've done a bit of research on this, which suggests that the problem has occurred to a number of Summitpost users recently, and that "bad" ads which have this behaviour have made their way into the AdSense system on a number of sites.

My question then is: do I need to worry about possible security implications of this (other than maybe not visit summitpost.org from now on)? Are there any measures specifically I need to take on my system to prevent possible security exploits that may have happened as a result of this?

I didn't have any other active logins at the time so I can't see an XSS/cookie stealing type attack would have occurred. After it happened I deleted my browser data "just to be sure".

This problem *only* happens on SummitPost - not on any other site, even one with ads - suggesting the problem is at their end; it's happened about 3 times recently.

Thanks,
Nick

---

### Post by Frogs Hair on 2015-03-10
Ghostery seems to disable this kind of add for me and there are other ad-blocking extensions as well, it's really a matter of preference . Unfortunately some sites allow words to be used as hyper links for advertising and hopefully the site checks the linked content. A safe ad could be replaced with something more invasive at a later date , but I would start with an ad-blocking extention if you aren't using one

---

### Post by bashiergui on 2015-03-10
+1 to ad blocking. Recently attackers have been going after ad networks which serve ads to lots of popular mainstream websites. It's definitely affecting more than just summitpost. (See this for some details [http://www.computerworld.com.au/article/565500/malicious-advertisements-major-sites-compromised-many-computers/](http://www.computerworld.com.au/article/565500/malicious-advertisements-major-sites-compromised-many-computers/)). 
AFAIK the malicious ads deliver windows exploits, but they could exploit flash or other cross platform apps. Best to stop it altogether by blocking ads.

---

### Post by vasa1 on 2015-03-10
> **bashiergui said:**
> ... but they could exploit flash or other cross platform apps. Best to stop it altogether by blocking ads.
And enable *click-to-play* for your browser's plugins if that is possible and not inconvenient.

---

