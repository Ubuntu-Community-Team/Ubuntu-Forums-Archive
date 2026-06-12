---
title: "Monitor out of range"
date: 2007-03-08
forum: General Help
---

### Post by crimsonmx on 2007-03-08
So my problem is that my monitor displays an out of range message directly after I see load screen and before login.

I run an ati radeon 9600xt, an agp card, and my mobo is a five year old asus model upon which I currently can't get any specifics

The first monitor message posted a range of two frequencies and "out of range"

The second message posted a different range of two frequencies and "out of range"

I dug around in the forums for a while and found that some had fixed their problem by adding in VertRefresh and HorizSync lines in xorg.conf, but I only can find my vertrefresh, so that option might be out unless someone knows the stats for a Xerox XR6-19DW.

I then saw that someone else installed the fglrx drivers and got theirs working, so I tried that, which produced a different monitor message

now it posts "1600x1200 60 khz" and out of range

I then added in my monitor's resolution into the modes section of the display section, but to no avail.

I'd be very grateful for some help with this issue

EDIT: Well, with some tinkering, found a solution

So first the fglrx drivers must be obtained

Then gtf must be run, in my case 1440 900 75 were the appropriate parameters

take the output from that (only the uncommented line is necessary) and put it into your fglrx monitor section 

then go to your screen (the fglrx one) and add the line Modes and the name of the modeline

reboot and be happy!

---

### Post by lhtown on 2007-03-08
It sounds like you are on the right track. You could add in the vertical refresh rate and play with the horizontal refresh until you get it right.

For instance, the first time, you could put a relatively narrow range. If it is good, then you could increase it perhaps by 5 or ten and try it again and keep playing with it until you find both ends. 

When you do find it, write it down and publish it on this forum for your benefit (when you have to do it again and have forgotten where you wrote it down) and for others.

I am not sure if the bit depth affects it or not. You could use a low one just to be sure until you get the horizontal resolution set.

---

### Post by dwanders on 2007-03-08
I don't know if this will help you or not, but I have had lots of trouble with my video stuff in the past. Looking up your monitor with a Google gives a Vert of 60-75, and a max res of 1440x900@75Hz no Horz (as you stated). I have a 19" LCD while not the same as yours, it is HZ 24-80 Ver 56-75 and a max res of 1280x1024 (just so you have a frame of reference) - I would set the vert to what you were given and experiment with the HZ. And the most significant piece of information, using:

dpkg-reconfigure xserver-xorg <cr> 

Before Ubuntu & Debian & the command above, I hated my video gear. Hope it helps.

---

### Post by crimsonmx on 2007-03-08
Thanks for the advice guys, but the issue grows curiouser and curiouser

I tried playing around with horizsync values, but then thought of trying out different resolutions in the modes section

First I tried 1024x768, which allowed me to get to graphical login and update and all that happy stuff

Then I tried 1280x800, which restored the the monitor message

Then I tried 1280x1024, which defeated the monitor message like it's younger cousin.

This also enabled a few extra resolutions under the system->preferences->screen resolution, unfortunately none of them widescreen

So it seems to fail for widescreen options

Does anyone know why this would happen?

---

### Post by crimsonmx on 2007-03-09
So after toying around with horizontal sync values, I am able to produce a few widescreen resolution options. Unfortunately, these options are greater than my lcd's ability to produce. Does anyone know how the gnome screen resolution app gets its values?

---

### Post by crimsonmx on 2007-03-09
So toyed around maybe too much
I changed the settings in system tools->configuration editor->...->screen/0/ and I want to know how to undo that without a graphical interface

EDIT: Just decided to do a clean reinstall, and then try out gtf, going to see how that goes

---

### Post by dwanders on 2007-03-09
Sorry, never used the Configuration editor - cant help ya there. I have only every used the dpkg reconfigure.

---

