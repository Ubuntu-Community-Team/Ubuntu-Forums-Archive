---
title: "Newiest Video Drivers for ATI Question."
date: 2006-08-11
forum: General Help
---

### Post by Patrick-Ruff on 2006-08-11
Hey all, it appears that my video drivers are properly working, I installed the newiest ones from ATI 8.27.10 and heres the question here, I'm getting 125FPS average for glxgears, Planet Pengiun Racer gets 94-120FPS on average. so it appears I'm getting accelleration, but with the older drivers I got 1500-1700 fps on the glxgears, what could this mean? it also appears that the 2d desktop environment is using the CPU primarally.


Would it be possible to check to see if there is graphical rendering on the desktop and/or if the CPU is doing the majority of the rendering? 5% CPU usage at all time on my linux laptop. my video card is an ATI Radeon Mobility X300 64MB PCI Express dedicated memory.


thanks to all that reply.

---

### Post by Patrick-Ruff on 2006-08-11
Thanks for all the wonderful replys.........

---

### Post by Anduu on 2006-08-11
As to your first question glxgears is a piss poor benchmarking tool...

To get an idea of how hard your CPU has to work put the system monitor applet in your panel and observe cpu usage while running opengl stuff in a window.

---

### Post by Patrick-Ruff on 2006-08-11
you see I think opengl is fine. I think its the 2d Rendering that is the problem. its like, whenever I interact with windows in any way the CPU usage jumps up VERY high. glxgears actually uses less then the average window.  the GNOME environment seems entirely dependant on the CPU, Dispite the video drivers working.

---

### Post by Patrick-Ruff on 2006-08-11
actually I take that back, when I play Planet Pengiun Racer it seems entirely dependant on the CPU as well, how does one fix this??????/

---

### Post by Anduu on 2006-08-11
What kind of usage numbers are you getting?

I know for a fact my drivers are installed and working correctly.Running PPR in a window at 800x600 with shadows on I get 70ish fps and 80-90% cpu usage...

---

### Post by Patrick-Ruff on 2006-08-11
yeah I'm running it in the same resolution and I get 80-124 fps on it. at 100% cpu usage.

---

### Post by Patrick-Ruff on 2006-08-11
also shouldn't the video card be doing the majority of the rendering and shit that the CPU appears to be doing? I remember using XGL and I had less CPU then the regular gnome session.

---

### Post by Anduu on 2006-08-11
> **Patrick-Ruff said:**
> also shouldn't the video card be doing the majority of the rendering and shit that the CPU appears to be doing? I remember using XGL and I had less CPU then the regular gnome session.

Well think of it this way...if not for your video card your processor would be at 100% and you would get like 1 frame per second.

Just because you have 3D acceleration doesn't mean your CPU is off the hook...there are still lots of other things it needs to be doing.

---

### Post by Patrick-Ruff on 2006-08-11
ok but it appears that there really isant that great 2d rendering. like everything seems a bit sloppy. is there anything I could possibly do to help this?

---

### Post by Patrick-Ruff on 2006-08-12
anyone have any ideas?

---

### Post by Seq on 2006-08-12
I remember having poor performance with my radeon 9200 using fglrx. I googled it, and according to the X.org wiki[1]:

> 2D performance is below of what the open source dri drivers do provide, but is still acceptable fast for everydays works.

-- ([http://wiki.x.org/wiki/ATIProprietaryDriver](http://wiki.x.org/wiki/ATIProprietaryDriver))

Also, the following link may come in handy:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#2D_speed](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#2D_speed)

---

### Post by Patrick-Ruff on 2006-08-12
I already have that thing set. the one that you had in your bottom link.

---

### Post by Patrick-Ruff on 2006-08-12
keep em commin guys! Ideas ideas ideas!

---

### Post by Anduu on 2006-08-12
Well I don't know what else to tell ya...

You peeked my curiosity so I just spent the last couple hours googling for ati/fglrx/xorg/linux tweaks and tryin stuff out.

Nothing I found no matter how obscure seemed to make one bit of difference...:-|

---

### Post by Patrick-Ruff on 2006-08-12
thats really odd. I mean on windows it appears that they know how to make it so the majority of the rendering is put on the video card, rather then the CPU. I found that my whole desktop environment felt a bit speedier on XGL. so I'll try that out today, thanks anyways guys.


if anyone figures anything out, feel free to PM me.

---

### Post by Patrick-Ruff on 2006-08-12
Ok nevermind. there is NO way my video drivers are /actually/ working properly. I get 3FPS on the Flurry screensaver. On windows when I had the same exact screensaver I had 100+ FPS average. Someone explain this to me please? And I really wan to get this fixed because I want to start using XGL/Compiz.

---

### Post by Greycloak on 2006-08-12
I have a Radeon 9200 and the gnome screensavers ran like crap.  I just installed xscreensavers and they all seem to run at full speed.

I have the 8.27.10 drivers and have had no troubles at all, except with Xgl/Compiz.

---

### Post by Patrick-Ruff on 2006-08-12
That's odd. I would have thought the first thing ubuntu would be trying to utilize perfectly would be the video drivers. I guess I'll see how it goes with XGL/Compiz then.

---

### Post by Patrick-Ruff on 2006-08-12
I'm going to test the XGL Installation, I'll report back after I get it working.

---

### Post by Ramses de Norre on 2006-08-12
> **Patrick-Ruff said:**
> That's odd.I would have thought the first thing ubuntu would be trying to utilize perfectly would be the video drivers.

> **Patrick-Ruff said:**
> I mean on windows it appears that they know how to make it so the majority of the rendering is put on the video card, rather then the CPU.

The answer is simple: the drivers for your video card are closed source and developped by the manufacturer, who puts a lot of effort in the windows drivers and gives a bit of information to FOSS developpers to make linux drivers, result: good windows and poor linux drivers..

---

### Post by cptnapalm on 2006-08-12
what does fglrxinfo tell you about your OpenGL implementation?  If it says Mesa, then that's your problem.

ATi's Linux drivers are so bad, that when I installed Ubuntu on a Compaq with a Xpress 200, I discovered that if I used those drivers, when I switched to a console, the drivers would crash the machine.  Anything which moved out of X, would crash the machine.  Including trying to shut the computer down.  They've been having a problem with this for about a year, on some configurations and they still haven't fixed it.

---

### Post by Anduu on 2006-08-12
That is why I use xorg-driver-fglrx exclusively....still not perfect but blows ATI's away...

---

### Post by cptnapalm on 2006-08-12
If it is fglrx, then it is the ATi driver, but with all the settings designed to work with the particular distribution rather than generically.  The machine that I have which dies if you are so bold as to switch to a virtual terminal or *gasp* logout, has the fglrx driver from the repository and this appears to have been a problem for about a year now, with some configurations.  Joy for me.

---

### Post by Anduu on 2006-08-12
> **cptnapalm said:**
> If it is fglrx, then it is the ATi driver, but with all the settings designed to work with the particular distribution rather than generically.  The machine that I have which dies if you are so bold as to switch to a virtual terminal or *gasp* logout, has the fglrx driver from the repository and this appears to have been a problem for about a year now, with some configurations.  Joy for me.

I have never had any major problems using xorg-driver-fglrx...only a couple of minor annoyances re BigDesktop...

It performs better and is more stable.

---

### Post by Ziox on 2006-08-12
i think this command test whether 3d rendering is enabled or not:

glxinfo | grep rendering

---

