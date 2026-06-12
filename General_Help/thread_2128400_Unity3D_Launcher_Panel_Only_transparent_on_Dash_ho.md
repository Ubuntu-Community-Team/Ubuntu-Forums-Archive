---
title: "Unity3D Launcher Panel Only transparent on Dash home click"
date: 2013-03-23
forum: General Help
---

### Post by Psil0cybin on 2013-03-23
I am trying to make the Unity3D Left Panel completely transparent, I have been able to get the top panel to be transparent successfully.
When I try and make the left panel with the icons transparent, I get a wierd brown Hue, I am unable to actually make it transparent
but the funny thing i when i click on the Dash Home and it opens up the Launcher, the bar and the launcher are completely transparent..

Is this a bug? Or am i doing something wrong with
MyUnity
and Compiz Config Settings Maanger

---

### Post by dino99 on 2013-03-23
does not know whats up with myunity nowadays, but its so easy to get a borked unity when tweaking ccsm, i would suggest to reset both compiz & unity to the default settings.
note that both unity & compiz will get major updates landing in a few days, so all your tweaks will be probably broken/incompatible/reset ...

---

### Post by Psil0cybin on 2013-03-24
Thanks for the tip, I'm going to give it a couple of days! 
Hopefully this can be fixed?
I think some how its just trying to tint the unity bar to the wallpaper...is that what is happening?
Is there a way to remove that?
I see that it tints differently with different wallpapers I set?
Thanks in advance.
psil0

---

### Post by mc4man on 2013-03-24
A completely trans launcher is easily done in 12.10 & upcoming 13.04, 12.04 was never fixed to allow this (though a fix is avail.

To do so in ccsm > unity plugin settings - 
set launcher opacity to 0.0000
open up the custom background color setting, leave color @ #000000 (black
to activate raise the opacity in custom background color setting **to anything above 0**

Note - the actual opacity setting in custom background color will not affect the launcher, it does affect the Dash.

Here I find I like no blur option better so use #000000 for color & raise it's opacity to around 190 or so

---

