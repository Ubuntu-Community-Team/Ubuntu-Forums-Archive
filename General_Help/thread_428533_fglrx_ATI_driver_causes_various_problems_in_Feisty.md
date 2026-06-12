---
title: "fglrx ATI driver causes various problems in Feisty..."
date: 2007-04-30
forum: General Help
---

### Post by Chriš on 2007-04-30
I'm running ubuntu 7.04 with a Radeon 9600. As soon as I install the driver "xorg-driver-fglrx" various problems surface.  When I System>Preferences>Font and click on the "Details" button, the windows dissappears. Also, my evince reader cannot open up pdf files, the whole OS freezes and I need to force kill the app.

Is this happening to anyone else? If someone is using 7.04 with a Radeon card and the xorg-driver-fglrx driver, can you reproduce the problem?

Thanks.

---

### Post by alexfarran on 2007-05-03
I have exactly the same problem.  Additionally, when I run evince at the command line I get these errors.

$ evince Wireframes_07.pdf 

(evince:13084): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

(evince:13084): Poppler-CRITICAL **: void poppler_page_render_to_pixbuf(PopplerPage*, int, int, int, int, double, int, GdkPixbuf*): assertion `pixbuf != NULL' failed

(evince:13084): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

(evince:13084): Poppler-CRITICAL **: void poppler_page_render_to_pixbuf(PopplerPage*, int, int, int, int, double, int, GdkPixbuf*): assertion `pixbuf != NULL' failed

(evince:13084): GdkPixbuf-CRITICAL **: gdk_pixbuf_new: assertion `width > 0' failed

(evince:13084): Poppler-CRITICAL **: void poppler_page_render_to_pixbuf(PopplerPage*, int, int, int, int, double, int, GdkPixbuf*): assertion `pixbuf != NULL' failed

---

### Post by dodgePT on 2007-05-03
I tried in vain for a week to get my radeon 9600 to work flawlessly with feisty (no beryl installed) with no luck.

I installed ATI proprietary drivers and everything seemed to be working fine, except for the fact that movies (even high-quality xvid ones) have shitty resolution (kinda blocky image) when in fullscreen mode (used all available movie players, also tried several video output settings, X11, OpenGL, etc, as suggested in several threads). Image is still blocky, i can see horizontal scan lines and cpu (PIV 3.0Ghz) gets almost 100% usage. Also, i couldn't activate desktop effects. Tried everything imaginable with no luck and i never got full quality xvid video as i get in XP.

Yesterday, after hours of xorg.conf tweeking and driver installing, i finally gave up. As much as i'd like to migrate definitelly to ubuntu, it became impossible since i use my PC to watch movies a lot.

Questions:
[B][U]- Does this have something to do with the xvid codec or is it all caused by the ati proprietary device driver (or any other ati linux driver available)?
- Is this an assumed bug by ubuntu's developing team and do they mean to do anything about it? (i know it depends on amd/ati to produce a more stable driver, but i had to ask)
- Anyone managed to solve the problems i described with any of the available ATI drivers? If so, which tutorial should i follow to definitelly solve the video playback problem?[/U][/B]

I depend on this to definitelly migrate to Ubuntu Linux, otherwise i'll have to get back to XP :( .

Ati device drivers for windows XP have several bugs, but it's much worse in Linux.
One thing i know for sure, i won't be buying ATI display adapters anymore, since they offer such a poor support to their linux costumers.

I think this issue should be solved as soon as possible for the sake of Ubuntu, since ATI has 22% of market share.

Thanks in advance for any help you can spare.

---

### Post by alexfarran on 2007-05-04
Video playback looks fine to me.  These are the settings in my xorg.conf that might be useful.  This works with fglrx and the open source driver.

```

Section "Device"
    Identifier	"ATI Technologies Inc RV350 AQ [Radeon 9600]"
    Driver		"ati"
    Busid		"PCI:1:0:0" 
    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"
EndSection

```

```

Section "DRI"
	Mode	0666
EndSection

```

If you want to use desktop effects then you need to use the open source driver or install XGL.  I'm running compiz with the open source driver and it works fine so far.

You'll need this in your xorg.conf
```

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

