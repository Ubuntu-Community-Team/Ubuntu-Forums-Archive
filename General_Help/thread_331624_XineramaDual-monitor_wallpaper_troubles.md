---
title: "Xinerama/Dual-monitor wallpaper troubles?"
date: 2007-01-04
forum: General Help
---

### Post by Old Pink on 2007-01-04
Hi, 

Using Xinerama to support my dual monitor setup. When choosing a wallpaper, the image is stretched across the two screens, ugly.

Is there any way I can set the wallpaper to be different for the two screens? Or even the same image, displayed twice?

- Pink

---

### Post by majoridiot on 2007-01-04
right click on the desktop and select "Change Desktop Background".  just under the wallpaper
viewing frame it says Style: with a drop down list.  there are a number of choices there.

if you want your current desktop image to display "individually" on each monitor, re-size it
(using the GIMP, etc.) to 1/2 the size of your desktop and then select style "Tiled".

---

### Post by Old Pink on 2007-01-05
> **majoridiot said:**
> if you want your current desktop image to display "individually" on each monitor, re-size it
(using the GIMP, etc.) to 1/2 the size of your desktop and then select style "Tiled".

Yes, that's the effect I'm after, although that's not displaying it individually, it's just an attempt to trick the system, which doesn't actually work considering the resolutions of the two monitors are different by choice. 

Any more suggestions?

---

### Post by bodhi.zazen on 2007-01-05
Several options:

First search the web for large, dual monitor wallpapers. For example, I have a space wallpaper I like with the earth on one monitor and the moon on the other ...

Second, use gimp to paste two small, single monitor wall papers side-by-side to make one large wallpaper.

Third, xfce and kde are dual monitor aware and you can set each monitor's wallpaper easily. I hope the gnome developers address this issue soon :(

Fourth, don't use twinview. If you set each monitor as a separate monitor you can move the mouse but not drag windows between monitors. This works well with all window managers, including fluxbox, icewm, gnome, kde, and xfce.

Here is how I do it: [How to Dual Monitor](http://www.ubuntuforums.org/showthread.php?&t=240150)

The newest nvidia drivers may do this via a gui, I have not tried that yet ...

---

### Post by majoridiot on 2007-01-05
when i had a two-head setup (i run 3 atm) i the used nvdida binary driver with twinview, which
gave two independent desktops that allowed for dragging windows between and maximizing
windows to just one screen.  if you run an nvidia card, this is what i recommend.

---

### Post by Old Pink on 2007-01-09
Guys, I don't use Nvidia. :) It's a SiS card.

---

### Post by Old Pink on 2007-01-11
Something should really be done about this by Feisty. :(

---

### Post by orb9220 on 2007-01-11
nvidia-settings has that under X Server Display Configuration.  Just click Configure button where it is showing Coniguration:Twinview.  It gives you choices of Diasabled,Separate X Screen,Twinview.

This for NVIDIA Driver Version:1.0-9746

Don't if it is there in earlier version.

---

### Post by Old Pink on 2007-01-11
> **orb9220 said:**
> nvidia-settings has that under X Server Display Configuration.  Just click Configure button where it is showing Coniguration:Twinview.  It gives you choices of Diasabled,Separate X Screen,Twinview.

This for NVIDIA Driver Version:1.0-9746

Ever think of reading a thread before replying? :rolleyes:

> **Old Pink said:**
> Guys, I don't use Nvidia. :) It's a SiS card.

---

### Post by surxain on 2007-03-14
> **Old Pink said:**
> Ever think of reading a thread before replying? :rolleyes:


take it easy. though I am using twinview, I couldn't find any easy way to solve this problem. I have just GIMPed a wallpaper.

---

