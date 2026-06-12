---
title: "display size."
date: 2015-06-18
forum: General Help
---

### Post by wyndlass on 2015-06-18
i changed the video size and now the display flashes and i can't do anything. i had to login as root to be able to do anything. what config files, or what not do i have to edit to get my account display back to default values? i have tried to find the right ones but can't seem too.  on my account , i can't even do ctrl-alt-f1-6. i don't wanna create another new account to fix this if i don't have to. i don't know if i can get grub to do a default video if i edit the command line stuff( not the press c one at boot). i just want to reset my display back to the size it was at install, w/o reinstalling, creating new account, or anything else that drastic. plz help me on this. also what i see on the screen is a narrowed version of the desktop besides the flashing. i set it to 800* whatever the width is that's standard for that mode and since then that's what's happening to my account display. thanx in advance.

---

### Post by deadflowr on 2015-06-18
Which display, the logged in desktop display or the grub display?
Those are different.
So it seems confusing...

And how did you try changing them, or it?

---

### Post by grahammechanical on 2015-06-18
How did you change the video size? Are you using a proprietary video driver? Proprietary video drivers usually come with a settings manager that we can use to detect displays and set the correct resolution.

You do not say which version of Ubuntu you are using. It makes a difference when it comes to giving instructions on how to use utilities with a graphical user interface. If you are using an open source video driver then System Settings has a Screen Displays utility that we can use.

In a terminal you can run this command

```
xrandr
```

It will give a printout similar to this
> 
graham@sdb1-Uplus1:~$ xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1920x1080      60.1*+   60.0     59.9     50.0     24.0     60.0     50.0  
   1440x480       60.1  
   1280x1024      75.0  
   1280x800       84.9  
   1280x720       60.0     59.9     50.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   720x576        50.0     50.1  
   720x480        59.9     60.1  
   640x480        75.0     72.8     59.9     59.9 

The resolution being used is marked with *

But how do you get to a desktop that is usable? At the Grub boot menu select Advanced Options for Ubuntu and then select recovery mode. At the recovery menu select resume and that will load Ubuntu using a fallback open source video driver that may give you a stable working environment.

By the way, it is 800 x 600 but it maybe that you set a wrong frequency.

Regards.

---

### Post by wyndlass on 2015-06-20
ok guys sorry about any confusion that i caused. i'm using vivid, it was the logged in display. i used settings<display and it doesn't give a freq setting for me.

[code]

Screen 0: minimum 8 x 8, current 1024 x 600, maximum 32767 x 32767
LVDS1 connected primary 1024x600+0+0 (normal left inverted right x axis y axis) 222mm x 130mm
   1024x600       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)


[code]


with xrandr what i get is above.  btw (fingers crossed) i think i have it fixed but need to several reboots to find out for sure. the last time i tried going into my account with it messed up, i was able to get menus so i went into settings<display and changed it there. i did also change the desktop that i was using from the normal ubuntu(unity) to gnome so i think that helped.. shrugs. i'll wait and see before i mark this solved. if i have trouble with this again i'll have this thread pdfed so that i can read it in root, i set root with a password so i could use it for things like this and was glad i did. i did try setting the system to 1024*768 instead of 800*600 but that really didn't help much unless i didn't reboot , only switch users. the only alternate driver that i'm using is for the intel atom n270 proc in my laptop. vivid did that itself when i insstalled

---

