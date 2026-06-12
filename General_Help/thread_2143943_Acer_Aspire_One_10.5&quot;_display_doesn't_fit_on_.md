---
title: "Acer Aspire One 10.5&quot; display doesn't fit on screen Ubuntu 13.04"
date: 2013-05-10
forum: General Help
---

### Post by Derelinquat fenestras on 2013-05-10
Hello,
I'm new to the forums, but have had this problem for a while so I'm just casting a net here.  If this is not the correct forum to place this thread, will someone direct me to the proper place. 

I own a Acer Aspire One 10.5" notebook.  I've had Ubuntu on it since 10.10 and for many programs, action menus are sometimes cut off at the bottom which prevents some level of functionality of my system.  I use Gnome session fallback 3.6 and the desktop fits, but not all of the programs and in standard Gnome the bottom notification bar is 1/2 cut off.  Not all programs have it, but sometimes after upgrading, different programs will be cut off at the bottom.  For instance this happened to GIMP recently, which is very bad news for me because I use it frequently.

I'm not sure where to start to fix this problem.  I don't know if it is some kind of graphics card issue, or internal program issue, or a resolution issue.

I have an Intel® IGD x86/MMX/SSE2 graphics card.

If anyone has any ideas, I'd be very appreciative.

---

### Post by Derelinquat fenestras on 2013-05-21
Well I never got a reply, but I did find a solution... albeit a temporary solution...

For anyone else who may have this problem:

I opened a terminal, I use guake terminal because it is so handy :)!  

I have a 10.5" screen with default resolution of 1024x600 and I needed to see 1024x724...

so I typed the command:

xrandr --output LVDS1 --mode 1024x600 --scale 1x1.1

this zoomed the display back on the y-axis so that I could at least visualize the bottom of the screen.
Unfortunately there is a problem... I could not move my cursor to positions below where the 600 resolution would have stopped, but I was able to control the menus/windows via the keyboard and make the necessary modifications.

after I was done, I reopened my terminal and entered:

xrandr --output LVDS1 --mode 1024x600 --scale 1x1

and my display returned to normal!

Good luck to all!

---

### Post by indy-h2 on 2014-03-27
Folks, I might be a bit late for this one ... I couldn't get to the bottom of Eclipse dialogs so used the following:

xrandr --fb 1024x768 --output LVDS1 --mode 1024x600 --scale 1x1.28 --panning 1024x768

It gives me 1024x768 without panning.

---

