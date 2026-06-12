---
title: "Flash-player Chromium"
date: 2014-04-16
forum: General Help
---

### Post by carl4926 on 2014-04-16
Don't exactly need help
But did anyone else experience same?
14.04 updated today 16th April
Chromium would no longer use the 11.2 flash
I had to switch to pepper flash

Maybe the update broke the link to 11.2 I didn't check

Also I notice the URL fonts are kinda big now

---

### Post by Double.J on 2014-04-16
Hi there,

Verified here.

[COLOR=#303942][FONT=Arial]Version 34.0.1847.116 Ubuntu 14.04 aura (260972)

Running 14.04 32bit. I don't use flash enough to be sure when it happened, but I last ran
```
apt-get upgrade
```night, and I noticed it this morning before I installed the *24 kernel update.
[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2014-04-16
Google will drop support for all NPAPI plugins for Chrome/Chromium for Linux in April/May. This means system flash, along with all mozilla plugins (= all multimedia plugins on Linux) will not work on these browsers. 

For Chrome this was supposed to happen in ver34 released in early April but it is postponed to ver35 in May, maybe it hits Chromium a bit earlier. For Chrome pepper flash is bundled, for Chromium you have to install it yourself (but non flash streaming will not work). One more reason not to use Chromium as the default browser.

To check if this is the reason why your flash doesn't work, try to watch Apple trailers in Chromium, if it has dropped NPAPI support then it won't work as it needs the quicktime plugin provided by Totem (which is a NPAPI plugin)

---

### Post by monkeybrain20122 on 2014-04-16
More [http://www.phoronix.com/scan.php?page=news_item&px=MTY2NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTY2NTg)

---

