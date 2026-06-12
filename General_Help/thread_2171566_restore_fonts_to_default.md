---
title: "restore fonts to default"
date: 2013-08-31
forum: General Help
---

### Post by snitz2 on 2013-08-31
I ran these 2 commands and now fonts on firefox look weird.

```
[COLOR=#0F1906][FONT=Lucida Grande]sudo rm /etc/fonts/conf.d/10-hinting-slight.conf[/FONT][/COLOR]
[COLOR=#0F1906][FONT=Lucida Grande]sudo ln -s /etc/fonts/conf.avail/10-hinting-full.conf /etc/fonts/conf.d/[/FONT][/COLOR]
```

How can I restore the fonts to their default state?

---

### Post by speartip on 2013-08-31
You haven't stated what version of Ubuntu you are using. But I use Ubuntu Tweak.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
Go to Tweaks/Fonts, & the click the box on the right hand side of each Font size, this returns them to there default value.

---

