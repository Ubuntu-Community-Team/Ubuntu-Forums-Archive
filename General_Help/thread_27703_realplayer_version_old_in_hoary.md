---
title: "realplayer version old in hoary"
date: 2005-04-17
forum: General Help
---

### Post by kcy29581 on 2005-04-17
Hi all,

How come the version in Ubuntu for realplayer is old (8.0.11) rather than 10? I know from Gentoo that there was a bug in reaplayer 10, maybe thats the reason?

Thanks.

---

### Post by heimo on 2005-04-17
[QUOTE=kcy29581]
                There is no spoon...
[/QUOTE]

There's no Realplayer. You probably installed realplayer 8 from marillat repository, which is (as far as I know) not part of Ubuntu. You can, however, install realplayer package from Ubuntu, which is actually Realplayer installer (you'll still have to download the realplayer from Real).

Hopefully this wasn't too confusing. :D

Cheers!

EDIT: You may want to check helix-player (alternative for the proprietary one).

---

### Post by kcy29581 on 2005-04-17
I don't use the marillat repository, I must be looking at the package you mentioned, the installer.

How does that work then? Does it ask you to download realplayer manually? If so it should have no problem with the latest realplayer which is 10.

I think I'll just install it with the .bin file supplied at real.com. I'm worried though, if I need to uninstall, will it be a pain as I'm not using synaptic?

I know of Helix Player, but it doesn't do the streaming media which I need.

Thanks

---

### Post by heimo on 2005-04-17
It asks path to the rpm version of Realplayer and then probably converts (with alien?) to deb for installing. I haven't tried it but I guess that uninstalling that installer (realplayer package) will also uninstall the real Realplayer. :D

At this very moment I'm streaming Nasa TV with totem (xine-lib), but I'm not sure about the version of codecs. Quality looks fine to me, but I don't know about support for html-embedded video.

EDIT: Hmm.. I don't have sound in my stream. :/ Normally I just use the windows media streams. (UPDATE: I think it's just this spesific stream, not the player or codec.)

---

### Post by kcy29581 on 2005-04-17
I think for html-embedded video totem people are working on a mozilla-based plugin, last time I checked on Google. I use VLC for everything now, but the only thing they obviously can't do is realmedia.

I do like totem though, the only reason I don't use it is the lack of the mozilla plugin.

So NASA TV outputs to a separate window and that works with Helix? I'm going to check their site now and get info.

---

### Post by heimo on 2005-04-17
No I was using totem for NasaTV. At least picture quality was fine, but seemed like they were having problems with sound (not so uncommon with NasaTV).

EDIT: And it plays both Realplayer and Windows media streams. Most of the time Windows media streams tend to be better.

---

### Post by kcy29581 on 2005-04-17
I've just been to the totem page... wow have they been busy since Gnome 2.8!!! They say the plugin works, and if you use the codecs supplied with mplayer, everything should work!!!

Thanks for all your help heimo

---

