---
title: "Performance (newby help)"
date: 2007-01-09
forum: General Help
---

### Post by shavenlunatic on 2007-01-09
Hi,

I'm new to Linux and Ubuntu, and if this query is in the wrong section, then please accept my apologies.

I will start with the basic system spect I am running

CPU: Athlon xp (clocked at 2.1Ghz if i remember)
RAM: 1GB of 400Mhz (DDR 3200)
Vid: Ati x1300 (8x AGP - 256 DDR2)

I have 3 HDD's in my PC so i decided to dedicate a whole drive to Ubuntu rather than messing around with partitions, this worked fine, and i can dual boot between the two operating systems (XP)

Only problem being is that the display is very laggy, redraw takes forever.  If i am scrolling in firefox it can take a few seconds each scroll.  And if i try to move a window around the desktop the redraw time is painful.

Now.. my PC is hardly top of the line but it should be able to redraw a window without struggling.

Things tried so far include:

downloading the ATI drivers, running them from the terminal (but I don;t know how to check if they have worked.. plus the ATI application taht has appeared in the Applications list won't run.

Disabled 2nd desktop

Removed background (scraping ther bottom of the barrel i know but hey)



Any ideas? (and please bear in mind that I am a competent PC user but a Linux "n00b")

Thanks in advance.

---

### Post by taurus on 2007-01-09
Maybe this guide will help.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by shavenlunatic on 2007-01-09
sorted, thats infinitely better.

I thank you... you sir.. are the daddy :)

---

### Post by Ramses de Norre on 2007-01-09
You can also set metacity to reduced resources to get faster redrawing and such, to do so: ```
gconf-editor /apps/metacity/general
``` and check the "reduced_resources" box.

---

### Post by shavenlunatic on 2007-01-09
i know I should really be starting a new thread on this.. but I found a guide to install xgl, and it seems to screw up half-way thru

i get to

```

Configuration

First we need to create a Xgl login session script, to do this, we create the following file startxgl.sh with this command in console:

sudo gedit /usr/local/bin/startxgl.sh

And copy this into the new file if you use Gnome:

#!/bin/sh
/usr/bin/Xgl :1 -fullscreen -ac -br -accel xv:fbo -accel glx:pbuffer &
sleep 4
export DISPLAY=:1
exec gnome-session

```

and it just goes all screwy, i am assuming its because the guide is assuming that i know how to use the editor... but who knows..

---

### Post by shavenlunatic on 2007-01-09
incidentally, one of the errors i get is:

E492: Not an editor command: 1 -ac -accel glx:pbuffer -accel xv:pbuff

---

### Post by Ramses de Norre on 2007-01-09
Then why don't you start a new thread?

The command to start the editor is in your very post (the line containing gedit), and if I were you I'd wait with xgl (which is not too stable) until you can find your way around gnome without it.

---

### Post by shavenlunatic on 2007-01-09
> **Ramses de Norre said:**
> Then why don't you start a new thread?


aye, probably wise...
> **Ramses de Norre said:**
> 
The command to start the editor is in your very post (the line containing gedit), and if I were you I'd wait with xgl (which is not too stable) until you can find your way around gnome without it.

aye, probably wise...



:D

---

