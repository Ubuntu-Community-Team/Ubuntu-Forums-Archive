---
title: "[SOLVED] Ugly resolution (reconfiguring xserver doesn't fix it)"
date: 2008-04-16
forum: General Help
---

### Post by angry_johnnie on 2008-04-16
Some guy in some thread once posted that Ubuntu likes to explode into a million fluffy kittens and pink ponies every time something goes wrong :-).

I guess that's pretty much what happened.

I can't complain, really, for I know that most, if not all of my problems, have been self inflicted.

I used to dual-boot Feisty and Gutsy, until Gutsy decided it was time to start hating me after a long, smooth, relationship :-).  I hadn't booted into gutsy for some time, so I thought it would be OK to wipe out my hard drive and do a clean install of Feisty.

But, I didn't want to go through all the updates and getting all my codecs and whatnot.  So I made a remastersys'd copy of my working installation.  This is something I'd already done before, with gutsy.  I have another computer that doesn't (and probably never will) have an internet connection, and that's how I get all my programs in it.

So, here's what happened:

After the installation was finished, I was able to reboot into a very functional Ubuntu Feisty.  But, the resolution is stuck at 1024x768.  I had been able to reconfigure xserver-xorg on my other computer (which has a really cheap 16mb graphics chip, and uses the vesa driver), so I thought it would be easy.  But it wasn't!

My laptop has an intel 945GM graphics card.  I'm using the i810 driver.  I've tried reconfiguring xserver-xorg with lots of different options (including a different driver), but nothing seems to get me out of 1024x768.

I wanted to be sure the problem wasn't related a bad iso image or a damaged dvd, so I installed it on my other computer.  I had no problem there.

So, that pretty much means (i think) the problem is related to my graphics card.

Now, the strange thing, is that a regular (non-remastersys'd) Ubuntu installation works fine.  And I get a really nice 1200x800 resolution.  So, I'm thinking maybe remastersys left something out.  Maybe I'm just missing something that was included with the original Ubuntu installation, but which remastersys decided to simply ignore.

So, I guess the real question is whether somebody knows what it is I'm missing.

1024x768 is not exactly insufferable.
It's just not quite what I'm used to.

If you can help me, I'll be forever grateful :-)
If not... well, I'll just cope with it :-)

P.S.  Sorry if I seem verbose... I have nothing else to do!

---

### Post by angry_johnnie on 2008-04-17
bump?

Has anyone with an intel 945gm chipset had a problem with resolution?

I found a certain i915 package at intel's website, but it wouldn't compile.  I have the appropriate kernel headers so I don't know.  Anyway, it would've given me an i810 driver, which is the one I'm currently using.

i found a package called 915resolution in synaptic.
I'll look for more information on it, later.

I'll try the xserver-xorg-video-intel package and see what happens, meanwhile.

I don't want to keep bumpin' my own thread :-).
So, if nothing works, and nobody here can figure it out, I'll just let it be.
It would be nice, though, to go back to my normal resolution :-)

---

### Post by Zorael on 2008-04-17
I'm not very familiar with reconfiguring xserver-xorg, but wouldn't it be possible to manually add the resolutions you want to the xorg file itself? (naturally, /etc/X11/xorg.conf.) I had to do this on Feisty with my laptop, since it wasn't correctly setting 1680x1050 as the best resolution. Gutsy gets this automatically; I don't have any resolution modes defined in my xorg.

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection     "Display"
		Depth      24
		**Modes      "1200x800" "1280x1024" "1024x768" "800x600"**
	EndSubSection
EndSection
```


There's also the chance that your driver polls the monitor for available resolutions and tries to pick out the best one, but the monitor isn't returning any. Apparently happens on certain TVs when you're trying to use them as main monitors. Your /var/log/Xorg.0.log should say so if this is the case. Example.
```
(--) NVIDIA(0): Connected display device(s) on GeForce 8600 GTS at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x1024"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768"; removing.
(WW) NVIDIA(0): No valid modes for "800x600"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
```


edit: As for the driver, pass! I'm more of an Nvidia guy.

---

### Post by angry_johnnie on 2008-04-18
Done!

Here's what I did. (in case somebody else runs into problems with a similar chipset)

1.  Stopped gdm from a virtual terminal
2.  Reconfigured xserver-xorg, and replaced the i810 driver with the good old Vesa one.
3.  Installed xserver-xorg-video-intel (it asked me to remove xserver-xorg-video-i810)
4.  Reconfigured xserver-xorg, and this time I chose the Intel driver
5.  Started GDM again.

And it worked!

I <3 Ubuntu... even when it turns into fluffy kittens :-)

---

