---
title: "Xorg trouble after Gutsy upgrade"
date: 2007-10-25
forum: General Help
---

### Post by jokr004 on 2007-10-25
Ok, so yesterday I upgraded from 7.04 to 7.10.  Ever since I did, I can't get dual monitors to work.  I am using an ATI Radeon 9800, and dual monitors with mergedfb worked just fine with Feisty.  I can't get dual monitors to work with the 'Screens and Graphics' tool.
Here is the xorg.conf I'm trying to use.
core-switchnet.com/xorg.txt
Anyone know why this might happen?

---

### Post by biosavvy on 2007-10-29
Not sure if you got this figured out yet, but I was able to use this post: [http://ubuntuforums.org/showthread.php?t=580967&highlight=Thinkpad](http://ubuntuforums.org/showthread.php?t=580967&highlight=Thinkpad)  to solve my problem.  

Here is the pertinent post:
> **Lil said:**
> Unfortunately it's not very well publicised that the open source 'ati' and 'radeon' drivers in the xorg.conf files no longer support dual displays via Xinerama in Gutsy.

What you need to do is use the xrandr tool now, we need a GUI for it as Screens and Devices does not configure using xrandr but using Xinerama, therefore attempts at dual screen using this will fudge things up.

Your best bet is to configure xorg.conf to use the 'radeon' driver and to boot the laptop in its basic 1024x768 32bit configuration.

Then when you've booted plug in your external display.

Open a terminal and type in:

xrandr (enter)

On that you will see that it detects the internal panel's (LVDS) capability resolution wise, and any device plugged into the VGA port (VGA-0) will also be detected.

If VGA-0 is showing resolutions up to 1280x1024 we're in business.

You need to edit your xorg.conf in one small way for this to work forever more.  In your xorg.conf find a section like this:

Section "Screen"
 Identifier “Default Screen”
 Device “ATI Technologies Inc Radeon…”
 Monitor “Generic Monitor”
 DefaultDepth 24
  SubSection “Display”
    Modes “1024×768&#8243;
  EndSubSection
EndSection

Under Modes enter:

  Virtual 2304 1280

(Where the width is the width of your two screen's max resolutions added and height is the height of the highest resolution display i.e.: (1024+1280)x1280)

The whole shebang should say:

Section "Screen"
 Identifier “Default Screen”
 Device “ATI Technologies Inc Radeon…”
 Monitor “Generic Monitor”
 DefaultDepth 24
  SubSection “Display”
    Modes “1024×768&#8243;
    **Virtual 2304 1280**
  EndSubSection
EndSection

Save and close xorg.conf

Restart the X server by logging in and out again (you might have to reboot but logging in and out should do it) and you'll never need to edit xorg.conf again. 

At the command line to keep the laptop panel (LVDS) at 1024x768 and to extend the desktop on the right with your external LCD at 1280x1024 you need to enter at the command line:

xrandr --output VGA-0 --right-of VGA-0
xrandr --output VGA-0 --mode 1280x1024

How does that work?

The only pain in the **** is that this does not survive reboots but it does work right; and it supports hot plugging etc.

You can read more on my blog here: [http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/](http://lilserenity.wordpress.com/2007/10/15/ecstatic-xrandr-12-means-decent-linux-screen-management-at-last/)

That explains mirroring, extending, even S-video output.

What we need though is a decent robust xrandr GUI and I think I'll see if I can do something myself.

I really hope this helps as I feel your pain on Linux screen management. Now I better start on that GUI!

Vicky

Hope that helps!

biosavvy

---

