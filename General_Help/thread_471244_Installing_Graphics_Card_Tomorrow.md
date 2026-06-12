---
title: "Installing Graphics Card Tomorrow"
date: 2007-06-11
forum: General Help
---

### Post by ashz on 2007-06-11
Hey Peeps,

Okay now its me asking for help for once lol,

Im buying a cheap AGP graphics card tommorrow (Nvidia 6200).  Will I have to recompile anything when i install it? At the moment it is using a intergrated SiS (i think) graphics chip.

Normally i am not one for eye candy but after seeing some of the great effects on my laptop which has an ATI 7500 Mobile Radeon i thought i would invest in a cheap card to try it out on my desktop.

All help will be great however small...

Cheers
Ash

---

### Post by hikaricore on 2007-06-11
In theory the Feisty restricted driver manager SHOULD be able to install the right video drivers for you.

But once you swap that card out and turn your pc back on, you X server will most likely bomb.

Easy enough to just run a:

> sudo dpkg-reconfigure xserver-xorg

From the command line though.  ^_^

And if the restricted manager fails at it's job, just download the latest drivers from Nvidia: [32bit]("http://www.nvidia.com/object/linux_display_ia32_100.14.09.html") / [64bit]("http://www.nvidia.com/object/linux_display_amd64_100.14.09.html")

Or use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"). (may not use the 100 series drivers yet, havn't checked, they just came out saturday)

---

### Post by ashz on 2007-06-12
I just wanted to say thank you very much for your help, worked perfectly!!!

Much appreciated,
Ash

---

### Post by ashz on 2007-06-12
Did i forget to mention that with a dirt cheap (£25) PNY 6200 graphics card, and a some helpful advice from hikaricore, i have compiz running and it looks bloody great!

Showed one of my friends who uses "That MS Product" and he is pretty pissed.

Mainly because he has shelled out about £200 on hardware upgrades to get a quarter of the effects that I have!!

In the process of trying to tempt him over to the darkside, we will see...though I see the major problem in getting him over being Games!!

Thanks again everyone, I love this community spirit, Linux Rocks, Ubuntu Rocks, and ner ner ner ner ner to Windoze!!

Laters
Ash

---

### Post by hikaricore on 2007-06-12
^_^

---

