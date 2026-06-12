---
title: "playerplug-in problems"
date: 2005-07-18
forum: General Help
---

### Post by Kimm on 2005-07-18
Hi,

I just downloaded and installed the latest version of mplayer plugin, I compiled it from source then made the install using checkinstall (after removing the old version). It compiles nicely and it seems to work... somewhat.

When I go to for example apple.com to watch a trailer the plugin doesnt work quite the way it used to before. Instead if embedding the video it creates a "semi-borderless" window in the top left courner of the screen and plays the movie there. Same thing happens in both firefox and mozilla. I tried upgrading firefox to the latest version from the website but with no luck, now I am back with the standard ubuntu version.

Heres a screenshot of mplauerplug-in playing the trailer for The Fantastic 4:

[http://i.domaindlx.com/MrKimm/mplayerplug-in.png](http://i.domaindlx.com/MrKimm/mplayerplug-in.png)

I'm quite puzzled! I'm thinking perhaps I missed some flags during configure?

Can anyone help?

---

### Post by Knome_fan on 2005-07-18
Hi, I don't know what causes this issue sorry, all I can say it works for me.

However, did you take a look at the following howto?
[http://www.ubuntuforums.org/showthread.php?t=44560](http://www.ubuntuforums.org/showthread.php?t=44560)

Maybe it'll give you an idea about what went wrong.

Good luck!

---

### Post by Kimm on 2005-07-18
Thank you, that worked great ^^

It might have been the lack of gecko-sdk but possibly the config file aswell

---

