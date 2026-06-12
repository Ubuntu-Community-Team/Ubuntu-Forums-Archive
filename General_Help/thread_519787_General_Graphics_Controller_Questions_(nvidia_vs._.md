---
title: "General Graphics Controller Questions (nvidia vs. Intel, etc.)"
date: 2007-08-07
forum: General Help
---

### Post by Jamie Jackson on 2007-08-07
I've got a Dell Latitude D620 [Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)]

I'm wondering if I've got everything configured that I should for this card. Some things I'm wondering:

[LIST=1]
[*]In Feisty, does it configure everything you need for Intel GMA cards, or does it do some sort of bare-bones install, after which knowledgeable users install other things?
[*]Is nvidia stuff mutually exclusive to Intel controllers? In other words, do people run nvidia software on top of intel cards, or does that not even make any sense.
[*]I've read about nvidia having an nvidia-settings package, where one can set gamma, brightness, etc.. Is there something similar for my controller? (I'm particularly interested in having the ability to make my screen *dimmer* than it's current *minimum* brightness.)
[/LIST]

Thanks,
Jamie

---

### Post by Jamie Jackson on 2007-08-12
(Bump)

I'd appreciate any information whatsoever pertaining to any question or any part of any question I've asked above. Birds-eye-view answers are also welcome.

Thanks,
Jamie

---

### Post by hardyn on 2007-08-12
1) it should be workable, but depending on the actual implementation by the notebook vendor, firmware versions etc. some people have had to put a little extra work into getting the desired resolutions.

2) yes, the drivers are specific to hardware, an nvidia driver will no work, and probably make a pretty good mess, of a system with intel hardware.

3) there are a few extra tools available for the intel hardware, but there are minimum and maximum specifications to all hardware, and it would not be responsible of a party creating a software to violate this hardware specifications; so.. i would not count on it.  (by brightness are you talking display brightness, or back light brightness?)

good luck.

---

### Post by hikaricore on 2007-08-12
> **Jamie Jackson said:**
> I've got a Dell Latitude D620 [Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)]

I'm wondering if I've got everything configured that I should for this card. Some things I'm wondering:

[LIST=1]
[*]In Feisty, does it configure everything you need for Intel GMA cards, or does it do some sort of bare-bones install, after which knowledgeable users install other things?
[*]Is nvidia stuff mutually exclusive to Intel controllers? In other words, do people run nvidia software on top of intel cards, or does that not even make any sense.
[*]I've read about nvidia having an nvidia-settings package, where one can set gamma, brightness, etc.. Is there something similar for my controller? (I'm particularly interested in having the ability to make my screen *dimmer* than it's current *minimum* brightness.)
[/LIST]

Thanks,
Jamie

1. Your Intel integrated chipset will be configured to use the "intel" driver or one of it's named sibling drivers by default.  Pretty much everything should work out of the box on this type of a card, be aware there are performance differences between linux and ***dows when using Intel cards for 3d applications on some systems.

2/3. Intel cards can not use Nvidia drivers.  There are however various tools for X, gnome, and command line that can adjust video options such as brightness contrast and gamma (xgamma might be useful to you).  Try searching Synaptic for this and other software.

---

### Post by Jamie Jackson on 2007-08-12
> **hardyn said:**
> 1) it should be workable, but depending on the actual implementation by the notebook vendor, firmware versions etc. some people have had to put a little extra work into getting the desired resolutions.
Oh right, I got that going. I think I needed to install 915resolution for that. I didn't know that was an Intel-specific thing.

> **hardyn said:**
> 2) yes, the drivers are specific to hardware, an nvidia driver will no work, and probably make a pretty good mess, of a system with intel hardware.

I actually thought my controller was nvidia in the beginning, and installed nvidia stuff, and configured xorg.conf for it, etc. I even got the nvidia control panel. It seemed to sorta work, except the nvidia control panel didn't really have any options. Anyway, I won't do that again, now that I know that they are not really meant to work with each other. I'm back to the Feisty stock config that has the Intel stuff in the xorg.conf

> **hardyn said:**
> 3) there are a few extra tools available for the intel hardware, but there are minimum and maximum specifications to all hardware, and it would not be responsible of a party creating a software to violate this hardware specifications; so.. i would not count on it.  (by brightness are you talking display brightness, or back light brightness?)

I had never considered the difference between display brightness and backlight brightness before. I guess I'm trying to reduce background brightness, as the display seems to be okay, but the backlight seems to shine through the pure black display. Thanks for asking about that point.

---

### Post by Jamie Jackson on 2007-08-12
> **hikaricore said:**
> 1. Your Intel integrated chipset will be configured to use the "intel" driver or one of it's named sibling drivers by default.  Pretty much everything should work out of the box on this type of a card, be aware there are performance differences between linux and ***dows when using Intel cards for 3d applications on some systems.

2/3. Intel cards can not use Nvidia drivers.  There are however various tools for X, gnome, and command line that can adjust video options such as brightness contrast and gamma (xgamma might be useful to you).  Try searching Synaptic for this and other software.

With regard to 3D: Is the stock Feisty behavior as good as it's going to get? Not that I have any complaints (yet), but maybe I will when I run some 3D stuff in the future (Beryl?).

That xgamma thing's pretty cool,  and playing with it, I see what it does. However, as hardyn helped me to understand, it seems that I'd want to adjust the background brightess, as opposed to display brightness (which xgamma seems to modify).

Thanks for the replies.

---

