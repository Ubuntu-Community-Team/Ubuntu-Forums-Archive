---
title: "Display Problems"
date: 2013-01-01
forum: General Help
---

### Post by Rokkross on 2013-01-01
I'm using an HP 6910p laptop with a Radeon X2300 graphics card. I decided to run xubuntu 12.10 on this notebook and have ran into some problems when installing/booting. I had to use the "nomodeset" option (I'm not sure if this card actually -does- support modesetting, but it certainly isn't working now) when installing and had to place the option in my /etc/default/grub file (otherwise it just stalls at a blinking cursor). I've gotten to a point where everything seems to boot just fine and I can run a graphical environment, but not in an ideal sense. The correct resolution isn't detected, and if I change the resolution to something else the color goes crazy. From what I've read the proprietary driver for ATI cards (fglrx) doesn't support this card, so I'm stuck with the free one. 

Is there anything I can do to fix the display problems? I'm guessing it's something I'll have to configure with the x server, but I'm not sure where to start or what exactly I have to do. Sorry if this sounds like a waste-of-time easy fix to any of you, I've never had problems like this before :P

---

### Post by sudodus on 2013-01-01
> **Rokkross said:**
> ... From what I've read the proprietary driver for ATI cards (fglrx) doesn't support this card, so I'm stuck with the free one ... Sorry if this sounds like a waste-of-time easy fix to any of you, I've never had problems like this before :P

I'm afraid that there is no easy fix in linux for your problem with that graphics card. Maybe a hard fix ;-) It is too bad, that the manufacturer is not supplying a good driver or information to make a good driver for their old cards. It seems that new cards are better supported (but it does not help you).

What resolution do you get? I guess the native resolution of the screen is 1280x800. What's the output of [FONT="Courier New"][SIZE="3"]xrandr[/SIZE][/FONT]? Maybe you can use xrandr for some advanced tweaking of your system, but I don't know enough to advice about that. Maybe someone else, who is reading this thread ...

Knoppix is known for good recognition and cooperation with hardware, also old hardware. It might be worthwhile to download and test it in your laptop. Knoppix is made to run live or live with persistence "poor man's install", and it runs well that way, although it is not quite the same as a regular installed system.

---

### Post by claracc on 2013-01-01
Perhaps information in this link [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) can help you.

---

### Post by Rokkross on 2013-01-01
> **sudodus said:**
> I'm afraid that there is no easy fix in linux for your problem with that graphics card. Maybe a hard fix ;-) It is too bad, that the manufacturer is not supplying a good driver or information to make a good driver for their old cards. It seems that new cards are better supported (but it does not help you).

What resolution do you get? I guess the native resolution of the screen is 1280x800. What's the output of [FONT=Courier New][SIZE=3]xrandr[/SIZE][/FONT]? Maybe you can use xrandr for some advanced tweaking of your system, but I don't know enough to advice about that. Maybe someone else, who is reading this thread ...

Knoppix is known for good recognition and cooperation with hardware, also old hardware. It might be worthwhile to download and test it in your laptop. Knoppix is made to run live or live with persistence "poor man's install", and it runs well that way, although it is not quite the same as a regular installed system.
The output of xrandr is:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1152 x 864, maximum 1152 x 864
default connected 1152x864+0+0 0mm x 0mm
   1152x864       60.0* 
   1024x768       61.0  
   800x600        61.0  

```The actual resolution of this display is 1440x900. I may try Knoppix, but I think I'll go ahead and try other options first. 
[QUOTE=clarcc]Perhaps information in this link [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) can help you.[/QUOTE]
Here's the thing, I don't seem to have an xorg.conf file. I have a directory with a few config files (/usr/share/X11/xorg.conf.d), but none of the files in  that directory look like they'll be of use.

EDIT: Whoops, didn't know that xorg.conf.d was standard. Still, I don't see anything relevant to the display in that directory.

---

### Post by sudodus on 2013-01-01
> **Rokkross said:**
> The output of xrandr is:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1152 x 864, maximum 1152 x 864
default connected 1152x864+0+0 0mm x 0mm
   1152x864       60.0* 
   1024x768       61.0  
   800x600        61.0  

```The actual resolution of this display is 1440x900. I may try Knoppix, but I think I'll go ahead and try other options first. 

Here's the thing, I don't seem to have an xorg.conf file. I have a directory with a few config files (/usr/share/X11/xorg.conf.d), but none of the files in  that directory look like they'll be of use.

EDIT: Whoops, didn't know that xorg.conf.d was standard. Still, I don't see anything relevant to the display in that directory.

I see that you get quite bad resolution now :-(

Unfortunately I'm not good at tweaking xorg.conf. I thought it's obsolete, but maybe that's the way to go with an old graphics card/chip. I wish you get good help from an expert on graphics :-)

---

### Post by Rokkross on 2013-01-01
Just for the sake of trying, I downloaded the xubuntu 12.04.1 LTS image and installed it to my system, and everything is working perfectly. It's probably not fair to say something was "broken" in 12.10, but something was definitely changed that put a small group of people at a disadvantage. 

I'm downloading updates now (for this release that is, I won't be moving to 12.10 any time soon), and hopefully something doesn't break when it finishes. If something does I'll try to find the package responsible and install an older version of it.

EDIT: No problems after installing updates. I'll mark the thread as solved.

---

### Post by sudodus on 2013-01-02
Congratulations to finding a good solution :KS

And thanks for sharing :-)

---

### Post by Calinou on 2013-01-02
> **Rokkross said:**
> Just for the sake of trying, I downloaded the xubuntu 12.04.1 LTS image and installed it to my system, and everything is working perfectly. It's probably not fair to say something was "broken" in 12.10, but something was definitely changed that put a small group of people at a disadvantage. 

I'm downloading updates now (for this release that is, I won't be moving to 12.10 any time soon), and hopefully something doesn't break when it finishes. If something does I'll try to find the package responsible and install an older version of it.

EDIT: No problems after installing updates. I'll mark the thread as solved.

You could've used Ubuntu Vibes' PPA (which should downgrade X for you) for doing that while keeping 12.10, thus having more updated packages such as Subversion 1.7...

---

