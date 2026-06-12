---
title: "out of range message on ubuntu 14.04"
date: 2018-03-02
forum: General Help
---

### Post by delfiler on 2018-03-02
so i recently installed ubuntu 14.04 on my server and the installation went off without a hitch but once it reboots and gets to the terminal i get the out of range message from my monitor i can login and once that is done fill in commands but i still have no screen so if i did make a typo or get anything i wouldn't have a clue so my question is how do i fix this?

edit: xrandr is not installed before hand apparently, reinstalling doesn't fix the problem

edit2: upgraded to 16.04 same resault

---

### Post by mörgæs on 2018-03-02
Hi, welcome to the fora.

Let's see the hardware. Please copy ```
sudo lshw -sanitize > lshw.txt
``` to a terminal, run it and post the results in CODE tags.

---

### Post by delfiler on 2018-03-05
> **mörgæs said:**
> Hi, welcome to the fora.

Let's see the hardware. Please copy ```
sudo lshw -sanitize > lshw.txt
``` to a terminal, run it and post the results in CODE tags.

i would love to, but still have no screen just black, i know about xrandr cause i have another server (still working and already in use) that does give screen, so that is how i found that out. and after carefully typing every single letter to install and adjust it, still nothing

edit1: it is a server so i can't just hop to different programs i just have the terminal and no GUI

edit2: other server is still okay as today is also the day for check up and reboot of a few servers to see if anything is of, i know odd but procedure of the company

---

### Post by mörgæs on 2018-03-05
Can you run the command from a live boot?

---

### Post by dragonfly41 on 2018-03-05
> [COLOR=#000000]still have no screen just black[/COLOR]

I also see an out of range monitor (but only when booting up).

I have to toggle [SuperKey}+[P key] to switch between "real" and "ghost" monitor.
Just keep hitting the combined keys (I believe there are three states and it cycles again).
[SuperKey] is the one with Windows icon.


[COLOR=#b22222]**[Adding further notes]**[/COLOR]

Exploring further .. I searched around to understand how this Super+P  toggle works.

[https://askubuntu.com/questions/68463/how-to-disable-global-super-p-shortcut](https://askubuntu.com/questions/68463/how-to-disable-global-super-p-shortcut)

You could try this on your other server.

Install dconf-tools package

Run dconf-editor

In the tree on the left, navigate org -> gnome -> settings-daemon -> plugins -> media-keys.

Also I see there is  org -> gnome -> settings-daemon -> plugins -> xrandr.

==============================

This is what I see when I run xrandr .. showing eDP1 and DP1 both connected when I only have one monitor.

```

xrandr
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
eDP1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 307mm x 230mm
   1024x768      60.00 +  75.03*   70.07  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    75.00    66.67    59.94  
   720x400       70.08  
   512x384       60.00  
DP1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 307mm x 230mm
   1024x768      60.00 +  75.03*   70.07  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08  
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

---

### Post by delfiler on 2018-03-06
> **mörgæs said:**
> Can you run the command from a live boot?
sadly i can't, i jsut get install and a few other options that are the same as install but, either adding something or different 
> **dragonfly41 said:**
> I also see an out of range monitor (but only when booting up).

I have to toggle [SuperKey}+[P key] to switch between "real" and "ghost" monitor.
Just keep hitting the combined keys (I believe there are three states and it cycles again).
[SuperKey] is the one with Windows icon.


[COLOR=#b22222]**[Adding further notes]**[/COLOR]

Exploring further .. I searched around to understand how this Super+P toggle works.

[https://askubuntu.com/questions/68463/how-to-disable-global-super-p-shortcut](https://askubuntu.com/questions/68463/how-to-disable-global-super-p-shortcut)

You could try this on your other server.

Install dconf-tools package

Run dconf-editor

In the tree on the left, navigate org -> gnome -> settings-daemon -> plugins -> media-keys.

Also I see there is org -> gnome -> settings-daemon -> plugins -> xrandr.

==============================

This is what I see when I run xrandr .. showing eDP1 and DP1 both connected when I only have one monitor.

```

xrandr
Screen 0: minimum 8 x 8, current 1024 x 768, maximum 32767 x 32767
eDP1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 307mm x 230mm
   1024x768      60.00 +  75.03*   70.07  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    75.00    66.67    59.94  
   720x400       70.08  
   512x384       60.00  
DP1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 307mm x 230mm
   1024x768      60.00 +  75.03*   70.07  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08  
HDMI1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
dconf-tools was already installed and got the same resault as you did with xrandr and with dconf-tools with the tree and what you also saw, so that didn't help much i guess
and the super+P key i have to try on the server with the problems

edit: super+p does seem to effect it but it doesn't seem to play nice

---

