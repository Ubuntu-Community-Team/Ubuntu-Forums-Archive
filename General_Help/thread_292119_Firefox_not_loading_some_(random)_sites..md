---
title: "Firefox not loading some (random?) sites."
date: 2006-11-03
forum: General Help
---

### Post by Armagguedes on 2006-11-03
Greetings.

I have come across a problem in Firefox both in WinXP/SP2 and now in a brand-new Kubuntu Edgy Eft: Firefox does not load certain websites, and there is no consistency across platforms.

In my WinXP box, Firefox (1.5.0.7) does not load a considerable number of sites, some of which i have never been to before (digg.com news links), and some that were once one of my homepages (ie, i loaded them very often, like tokyotosho.com). On the other hand, IE6 loads everything well (as well as IE can though), as well as Opera 9.02.

In my KDE-Edgy laptop (fresh install), so far Firefox (2.0-ubuntu1) does not load only slashdot.org, and i was able to access it up until about a week ago. Then, all of a sudden, it just died on me. However, Konqueror loads slashdot just fine.

Any ideas on what may be causing this? I'm completely at a loss. I've done the regular tweaks, like the "network.http.pipelines" (or wtv) set at "8" and so forth. Also, stuff like NoScript allows for java in /., and AdBlock Plus doesn't show any problematic settings (also, i have none of these extensions in WinXP).


Thanks for the input.
Cheers

---

### Post by marianom on 2006-11-03
Hi there.
See if these helps:
[http://kb.mozillazine.org/Error_loading_websites](http://kb.mozillazine.org/Error_loading_websites)
[http://forums.mozillazine.org/viewtopic.php?t=258042](http://forums.mozillazine.org/viewtopic.php?t=258042)

---

### Post by puppy on 2006-11-03
Ah, if digg is causing you problems it *might* be the mtu of your machine being too high - I had to lower mine to get digg.com to load, and to access my email - there are various solutions on the forums but post here if you don't have any luck finding one and I'll help you out  ;)

---

### Post by Armagguedes on 2006-11-03
> **puppy said:**
> Ah, if digg is causing you problems it *might* be the mtu of your machine being too high -  (...) 

What the hell is the MTU? 
Also, digg itself is _not_ causing problems. What i meant was that i can't access certain websites, most of them are linked from digg, since it is where i get my news.

---

### Post by Armagguedes on 2006-11-03
OK, so far, no progress.

In my connection settings, "direct connection" is enabled. Cache was cleared. IPv6 disabled did nothing. "network.http.pipelining" was also a wrong turn. 

Still nothing. God damn it.
[]("http://kb.mozillazine.org/Network.http.pipelining")

---

### Post by Armagguedes on 2006-11-03
Ok.
Now this is getting _weird_.

I still can't access [http://slashdot.org/](http://slashdot.org/) , but it seems i have no problem accessing the different /. sections (ie., [http://linux.slashdot.org/](http://linux.slashdot.org/) [http://yro.slashdot.org/](http://yro.slashdot.org/) etc).

I fact, i currently have an open tab on [http://news.slashdot.org/](http://news.slashdot.org/), and updated my settings to show all sections on the top left corner frame. I can't seem to be able to list on said frame "news", "entertainment" and "technology".

Oh well, at least there is some progress. Now WhyTF can't i just go to the main section directly.

Cheers.

---

### Post by llevolj on 2008-07-12
I had a similar problem with Firefox and Slashdot on my Mac.  I cleared all the "Private Data" except the cookies and now it loads great.

---

