---
title: "Is there any way to get scroll bar arrows back - Ubuntu 18.04.1"
date: 2018-11-24
forum: General Help
---

### Post by michko2 on 2018-11-24
Okay, first let me say that I'm coming back to Linux after a few years away.  As I'm sure you can tell from the question, it has been a while.

I also know that the scroll bar arrows were taken out intentionally.  From what I've read this was to better facilitate touchscreens.  

I get all of that.  However, I'm disabled.  Had a neck operation that went sideways.  I won't bore you with all of the details, but please understand that to me, those scroll bar arrows are dang close to being a necessity.  

I can't find any way to get them back.  I don't want to go to an earlier version either.  I actually thought they may be included in the Universal Access settings, but no such luck.

Please, don't give me some of the "holier-than-thou," snobbish replies about this is a move forward, go buy a new mouse with a scroll bar (I'm on a laptop that fits my particular situation), that I have read on other forums.  If that makes anyone upset, tough.  I read way too many replies that showed an attitude I didn't expect from the Linux community.  

Anyway, all of that aside, having scroll bar arrows would be very helpful to me as a disabled person stuck on the laptop setup that I have. 

Does anyone out there know of any way to bring back the scroll arrows?  Please.

Thank you.

Walt

---

### Post by 23dornot23d on 2018-11-24
I am the least snobbish person on here ....... so will try to help ......... but a little more information is required first .....

sudo apt install inxi

inxi -F

and please post back the results .......... things needed are the desktop you are using and gtk2 or gtk3

I have looked around for solutions and most I am finding require editing config files or css files ....... but !!! I have tried them on my own system
and am not getting them to work as of yet ......... so for now this is just something for information - someone else with programming experience might
be able to pick it up from here - once a little more information has been given

As someone might be able to write a small script file or something that will make things simple ............ best of luck with more replies once they know
what desktop you use ....... ie.  gnome-shell,  kde , mate , ubuntu , xfce , lxde  etc  as it may change the reply you get back.

```

The arrows are a bit more complicated...
Edit the gtk-2.0/gtkrc file for the theme you are using.

ADD THIS LINE:  **GtkScrollbar::stepper-size = 18**


GtkScrollbar::has-backward-stepper = 1
GtkScrollbar::has-forward-stepper = 1
**GtkScrollbar::stepper-size = 18**
GtkScrollbar::slider-width = 18
GtkScrollbar::trough-border = 1
GtkScrollbar::activate-slider = 1
GtkScrollbar::min-slider-length = 24


Change these lines to 1, not 0
GtkScrollbar::has-backward-stepper = 1
GtkScrollbar::has-forward-stepper = 1



That is for the gtk2 programs. For gtk3 programs, edit the gtk-3.0/gtk-widgets.css file, at about line 1656

.scrollbar {
    background-clip: padding-box;
    -GtkRange-trough-border: 2;
    -GtkScrollbar-has-backward-stepper: **1**;
    -GtkScrollbar-has-forward-stepper: **1**;
    -GtkRange-slider-width: 10;
    -GtkScrollbar-min-slider-length: 30;
    -GtkRange-stepper-spacing: 0;
    -GtkRange-trough-under-steppers: 1;
}

```

---

### Post by Frogs Hair on 2018-11-24
Some themes for Xubuntu/XFCE still include scrollbar arrows. It appears many of the theme developers have excluded scrollbar arrows all together and this includes 3rd party themes as well. It's not a feature that can be enabled or disabled from dconf editor if the theme doesn't include it.

---

