---
title: "Compositing with Metacity"
date: 2006-10-28
forum: General Help
---

### Post by Gannin on 2006-10-28
A lot of people are trying to use Compiz or Beryl for their compositing, but according to Gnome's website, even though compositing isn't fully supported by Metacity in Gnome 2.16, it's still partially supported with a few effects if Metacity is compiled with the right options.

When looking in the gconf-editor of Edgy, I notice that there is now an option to have Metacity act as a compositor.  Does that mean that Metacity was compiled with compositing support for Edgy?  Has anyone gotten this to work?

---

### Post by woedend on 2006-10-28
metacity has very weak effects....nothing at all similar to beryl or compiz.  i havent used edgy enough to play with it, but the settings are most likely still there, they were in breezy of all things.

---

### Post by Gannin on 2006-10-28
Checking Dapper with gconf-editor, it doesn't have the same compositing option for Metacity that Edgy does.

---

### Post by VFiend on 2006-10-28
It has to be enabled at compile time and it isn't enabled in Ubuntu's builds. There's talk that it'll be more ready in GNOME 2.18, though.

---

### Post by Gannin on 2006-10-28
According to Gnome's website, it's supposed to be completely ready by Gnome 2.18, so that should be interesting.

---

### Post by woedend on 2006-10-29
you must understand that metacity is gnome's default.  gnome is made for the office/everyday user.  Wobbling windows and weird fire effects,cool as they are, will not be seen.  Most likely just slightly functional effects im guessing.

---

### Post by jonasan on 2006-10-30
I like to keep things simple with Linux. I tend to screw systems up with too much (noobie) tuning.

Really all i want is the rotating Desktop. I find it useful.

I was after using AIGLX, I like what it stands for as opposed to GLX. I understand AIGLX is intergrated with Gnome 2.16, and from the sounds of it Metacity Composition from 2.18. Therefore, are we going to be seeing a 3D ready, albeit without native graphics driver support, Gnome Desktop some time soon?

---

### Post by Gannin on 2006-10-30
I think when we get Gnome 2.18, providing you have drivers that support it, the compositing features of Metacity will be able to be turned on and off just by selecting an option.  If compositing is compiled into Metacity, this is already possible through gconf-editor, though I expect when Gnome 2.18 is released, there will probably be a configuration window under the System > Prefrences menu to make things a bit easier.

As for the effects of Metacity with compositing, according to Fedora's website about AIGLX, where they have a few videos of effects with Metacity and compositing posted, it'll have all the wobbly goodness of other compositing managers, and I suspect it'll have options to choose different effects, considering the page shows two different minimization effects.

---

### Post by munzli on 2006-11-13
aiglx is built into xorg 7.1 and can be ebabled in the xorg.conf. if you then use the freedesktop version of compiz you can enable/disable compiz/metacity to your likening... very cool, and the settings screen for GL desktop is very simple too ;) you should try it

---

