---
title: "Nvidia Gforce FX5500 right drivers to work with Svideo output"
date: 2014-09-14
forum: General Help
---

### Post by frank18 on 2014-09-14
Hi guy; i've got the nvidia GforceFx5500 video card in xubuntu 14.04 and installed with the drivers from X.xorg  
  i have Vga picture ok,but the Svideo out is just black&white,
strange when i boot till the Dell logo  and in  the Bios set up  it  shows color in the Svideo but after that just black&white pic on  Svideo.
You guys know any other Nvidia drivers that could resolve color situation,thanks

---

### Post by Slim Odds on 2014-09-14
Sorry to be the one to give you the bad news, but the FX5500 is a very ancient card. The last Nvidia driver to support it was 173.1439 released in almost 2 years ago. Are you trying to use the Nvidia driver or the generic one?

---

### Post by frank18 on 2014-09-14
> **Slim Odds said:**
> Sorry to be the one to give you the bad news, but the FX5500 is a very ancient card. The last Nvidia driver to support it was 173.1439 released in almost 2 years ago. Are you trying to use the Nvidia driver or the generic one?

thanks i use whatever install from scratch i tried the legacy but pc  doesn't boot see pic attach.

---

### Post by frank18 on 2014-09-14
here a better pic

---

### Post by grahammechanical on 2014-09-14
It might be a screen resolution thing. The splash screen and BIOS settings utility use a low resolution. Especially a low number of colours in the colour palette. The S-video cable might not be able to match the output of the VGA port. You may need to change the colour depth.

[http://en.wikipedia.org/wiki/S-Video](http://en.wikipedia.org/wiki/S-Video)

> [COLOR=#252525][FONT=sans-serif]By separating the black-and-white and coloring signals, it achieves better image quality than [/FONT][/COLOR][composite video]("http://en.wikipedia.org/wiki/Composite_video")[COLOR=#252525][FONT=sans-serif], but has lower color resolution than [/FONT][/COLOR][component video]("http://en.wikipedia.org/wiki/YPbPr")[COLOR=#252525][FONT=sans-serif].[/FONT][/COLOR]

Regards.

---

