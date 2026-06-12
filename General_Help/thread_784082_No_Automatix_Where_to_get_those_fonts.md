---
title: "No Automatix? Where to get those fonts?"
date: 2008-05-06
forum: General Help
---

### Post by detroit/zero on 2008-05-06
The only thing I've been using Automatix for since Edgy is to get a package of extra fonts. Not the MSTTCOREFONTS selection, though that's nice, too.. but there was another package called "extra fonts" or some such thing. I can't seem to find hide nor hair of it anywhere online now. There were a few fonts in that package that I used extensively in my theme and for other purposes, and since upgrading to 8.04 the other night I'm trying to get everything back the way I like it.

Anybody have any idea on where I can find that font package, short of hunting them down one by one and installing them individually?

---

### Post by mano cazalet on 2008-05-06
msttcorefonts is the name of the package and it is official multiverse repositories. Make sure they are enabled before search in synaptic

I would also recommend ttfliberation fonst, they are really useful

and also you might want to check this [blog entry]("http://ubuntusite.com/fix-get-best-firefox-font-linux/")

---

### Post by detroit/zero on 2008-05-06
Right, right. I already have the MSTTFCOREFONTS installed. That's *not* what I'm looking for.

There was an extra font package in Automatix that had fonts like Junkyard, Canadian Prime Minister, Dirtybakersdozen, Neuropol, Neuropolitical, on and on.. There were 70 or 80 fonts in this download. Maybe more.

The liberation fonts was a fast download, and not what I was looking for. This package I downloaded in Automatix took a solid half hour to download and install. Here at the [Automatix Wiki available packages list]("http://www.getautomatix.com/wiki/index.php?title=Software_and_Tweaks"), the seventh item - *Extra Fonts (including MS Fonts, Liberation Fonts) 64bit* - is the one I'm after.

Note it says it is "_including_ MS Fonts and Liberation fonts". There were a ton of others there, too.

Where do I find that ton of others?

---

### Post by mano cazalet on 2008-05-06
oh now I see,

i believe some of them were agfa-fonts, and you can find these in open suse packages

as the other ones maybe the only solution is to download them one by one:

[http://www.dafont.com/top.php](http://www.dafont.com/top.php)

[http://www.1001freefonts.com](http://www.1001freefonts.com)

or maybe install gutsy in a virtualbox, install automatix, download the fonts, save them and transfer to your hardy

---

### Post by compiledkernel on 2008-05-06
[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by detroit/zero on 2008-05-07
> **mano cazalet said:**
> []("http://www.1001freefonts.com")or maybe install gutsy in a virtualbox, install automatix, download the fonts, save them and transfer to your hardy

That's an interesting, right-in-your-face, common sense, plain-to-see, totally obvious workaround.

Which explains why I didn't think of it.

I think I'll do it that way. Thanks for the idea!

---

### Post by detroit/zero on 2008-06-24
After searching around, I stumbled onto this blog post: [http://linuxondesktop.blogspot.com/2008/03/ubuntu-and-fonts.html](http://linuxondesktop.blogspot.com/2008/03/ubuntu-and-fonts.html) which got me to do some more searching. Turns out the specific fonts I was after are part of packages now available in synaptic.

Opening Synaptic, searching for "ttf", and selecting the following packages gave me the fonts I was looking for, plus a lot more:

ttf-georgewilliams
ttf-larabie-deco
ttf-larabie-straight
ttf-larabie-uncomon
ttf-larabie-liberation
ttf-sjfonts
ttf-tuffy
ttf-ubuntu-title
ttf-xfree86-nonfree

Getting those packages through Synaptic will give you *hundreds* of fonts, or just:
```
sudo apt-get install ttf-georgewilliams ttf-larabie-deco ttf-larabie-straight ttf-larabie-uncomon ttf-larabie-liberation ttf-sjfonts ttf-tuffy ttf-ubuntu-title ttf-xfree86-nonfree
```

---

