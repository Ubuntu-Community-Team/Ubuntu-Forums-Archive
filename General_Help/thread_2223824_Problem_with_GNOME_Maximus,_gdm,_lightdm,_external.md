---
title: "Problem with GNOME Maximus, gdm, lightdm, external screen."
date: 2014-05-13
forum: General Help
---

### Post by bluepicaso2 on 2014-05-13
Hello,
So i installed a fresh copy of ubuntu 14.04, and then realised there was no GNOME desktop, so installed it too.
All worked fine,then one day i though of using Maximus to remove window decorations from maximixed windows.
**Problem 1: MAXIMUS**
both shell extension and maximus (found on default repo) created a problem.
ONce the window is maximized it becomes invisible, and screen display freezes, top panel works, but other then that does not.
moving other windows over it looks like the attachment screenshot (but today i cant even switch windows).
[ATTACH=CONFIG]253111[/ATTACH]
**PROBELM 2**
when i installed gome i could see the new gnome login. It worked for like 3 days and gone again, today. I get the unity greeter with option to choose between unity, gnome etc.
I tried ```
sudo dpkg-reconfigure lightdm
```
but nothing fixed.

**PROBLEM 3**
I use an external screen, and wnat to make it primary for login screen too. but the Unity login comes on laptop.
**Though gnome login screen always came on the external screen**.

i am tired of this. Dont want to use unity, its heavy.
I also tried using xfce desktop its has issue with indicators and volume keys did not work.
also installed mate dektop too, its panel never appreared.

not sure what to do. its hidering my work  a lot. Hope to find a solution

Thank you

---

### Post by buzzingrobot on 2014-05-13
Gnome is moving to client-side window decorations. ([http://blogs.gnome.org/mclasen/2013/12/05/client-side-decorations-in-themes/](http://blogs.gnome.org/mclasen/2013/12/05/client-side-decorations-in-themes/)). Perhaps Maximus is not compatible with that.

I'd recommend installing Ubuntu Gnome if the goal is to run Gnome. ([http://ubuntugnome.org/download/](http://ubuntugnome.org/download/)). I've found it a very nice implementation of Gnome 3.10.  (I don't recommend bumping up to 3.12 from the PPA's, at least not yet.)

Mate should be installed using the instructions here: [http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download). Ubuntu users are better off installing Mate 1.6.  Ubuntu is currently missing a few dependencies needed to allow the recently released 1.8 version of Mate to function without breakage in a few packages.

---

### Post by bluepicaso2 on 2014-05-13
just installed mate desktop again, works fine.
fightting with firefox font redering, currently

---

### Post by buzzingrobot on 2014-05-13
Mate's default font rendering choice is often poor.  Adjust it via System->Preferences->Appearance->Fonts.  On Ubuntu,  check "Subpixel Smoothing (LCD's)" and then Subpixel smoothing and Slight hinting (the latter two on the "Details" panel.)

Choice of fonts is subjective.  The Ubuntu family looks good, as does Droid.  I use a lot of Open Sans (from Google Fonts) with the Semibold style.

---

### Post by bluepicaso2 on 2014-05-13
did that and a few more tweaks not bolder fonts in firefox are ugly.
[ATTACH=CONFIG]253120[/ATTACH]
the fonts in chrome are slight different very minute difference,

---

### Post by buzzingrobot on 2014-05-13
Don't know what fonts Tweetdeck is using there. You can highlight a word, right click, select "Inspect Element" and then "Fonts" in the display to see. If a site is using a font that is not on a system or that it does not download itself, then appearance is usually degraded because a fallback is substituted. That fallback will be specified in the page's CSS.

Turning off hinting on bolded fonts sometime improves appearances.  You need to insert this snippet from the Arch wiki ([https://wiki.archlinux.org/index.php/Font_configuration#Disable_auto-hinter_for_bold_fonts](https://wiki.archlinux.org/index.php/Font_configuration#Disable_auto-hinter_for_bold_fonts)) in either ~/.fonts.conf or in /etc/fonts/local.conf.  The rest of that wiki page is a very good explanation of how Linux handles fonts.

---

### Post by bluepicaso2 on 2014-05-13
Na nothing , its actually for all bold font system wide, doesn't help.

---

### Post by buzzingrobot on 2014-05-13
Sites specify font face, style, etc. You can tell the browser to override that and use only fonts you specify, but that can lead to broken page displays.

I see Tweetdeck using some Helvetica, Helvetica Neue, and Lucinda Grande, faling back to generic sans-serif (Deja Vu Sans in Ubuntu.)  (At least on their landing pages; I don't have an account.)  Those are Apple fonts.  Helvetica is usually mapped to Arial if it's installed, not that the two look much alike.

---

### Post by bluepicaso2 on 2014-05-13
well this solved it
[http://www.webupd8.org/2013/06/better-font-rendering-in-linux-with.html](http://www.webupd8.org/2013/06/better-font-rendering-in-linux-with.html)

---

### Post by buzzingrobot on 2014-05-13
Yes, the Infinality patches take a different approach.  I use it if I'm not running a recent Ubuntu or a derivative.  Be sure to explore the many settings options available. 

Infinality has not been updated for a year, so it is a few versions behind the Freetype library it patches. Dunno what that means dwon the road.

---

