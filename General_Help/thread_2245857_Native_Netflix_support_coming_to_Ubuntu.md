---
title: "Native Netflix support coming to Ubuntu"
date: 2014-09-26
forum: General Help
---

### Post by VE6EFR on 2014-09-26
[http://www.geekssharingspace.org/2014/09/ubuntu-developers-releases-updated-nss.html](http://www.geekssharingspace.org/2014/09/ubuntu-developers-releases-updated-nss.html)

I did a search but didn't see this posted as of yet. With being more of a Ubuntu user and not really one that digs deep into the operating system innards, will this rollout come automatically or would this be something that I need to update manually?

---

### Post by VE6EFR on 2014-09-26
I guess I should have looked a little closer. The answer was found in a link in the article itself - [http://www.ubuntu.com/usn/usn-2350-1/]("https://wiki.ubuntu.com/Security/Upgrades")

---

### Post by deadflowr on 2014-09-26
nss was updated to the wanted version recently
[http://www.ubuntu.com/usn/usn-2350-1/](http://www.ubuntu.com/usn/usn-2350-1/)


So now the onus is on the netflix dev to convince the netflix devs to lift the block on Ubuntu, et al.

---

### Post by yancek on 2014-09-26
You can use google-chrome-beta to watch Netflix in html5 with the libnss libraries.  Instructions at the site below if you are interested.  Works a lot better for me than wine-pipelight.

[http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins](http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins)

---

### Post by jawilljr2 on 2014-09-26
> **yancek said:**
> You can use google-chrome-beta to watch Netflix in html5 with the libnss libraries.  Instructions at the site below if you are interested.  Works a lot better for me than wine-pipelight.

[http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins](http://www.omgubuntu.co.uk/2014/08/netflix-linux-html5-support-plugins)

Those instructions are old.  All you have to do is update your system to get the latest libnss files (3.17).

[Source]("http://www.omgubuntu.co.uk/2014/09/ubuntu-rolls-updated-nss-library-native-linux-netflix-support")

Also you no longer need Beta or Dev vsrsion...the latest Chrome stable (ver 37) works.

[Source]("http://www.webupd8.org/2014/09/nss-updated-to-allow-native-html5.html")

> [COLOR=#333333][FONT=Arial]Of course,[/FONT][/COLOR]** Google Chrome (stable - you no longer need Chrome Beta or Dev) is still needed.**

What is nice is that Canonical also updated those files for Precise. I can confirm that it also works on Precise.

---

### Post by Habitual on 2014-09-27
Google Chrome [COLOR=#303942][FONT=DejaVu Sans]Version 37.0.2062.120 (64-bit)[/FONT][/COLOR]
 [COLOR=#303942][FONT=DejaVu Sans]User-Agent Switcher for Chrome[/FONT][/COLOR][COLOR=#303942][FONT=DejaVu Sans] [/FONT][/COLOR][COLOR=#303942][FONT=DejaVu Sans]1.0.36[/FONT][/COLOR]
 Mozilla/5.0 (Windows NT 6.3, Win64, x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/38.0.2114.2 Safari/537.36

---

