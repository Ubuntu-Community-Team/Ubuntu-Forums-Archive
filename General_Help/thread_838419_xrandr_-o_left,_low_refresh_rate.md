---
title: "xrandr -o left, low refresh rate"
date: 2008-06-23
forum: General Help
---

### Post by deadguy on 2008-06-23
I just got a 1920x1200 lcd, which I have configured in portrait mode via `xrandr -o left`.  But now the framerate is really slow, and I can watch the fame updates cascade across the screen (from the original top to bottom, or right to left in portrait mode).  Is there anything I can do to speed it up?  Is it a configuration problem, a limitation of my graphics card, or the monitor itself?

Monitor: HP w2408h
Card: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
Computer: DELL Inspiron E1505


thanks

---

### Post by deadguy on 2008-06-23
This is surprising to me, but the refresh is much faster and smoother when I use XDMCP to log in to a virtual machine!  I'm not sure how that could be.  At first I thought maybe the X instance created for the XDMCP session was being automatically configured for portrait mode better than xrandr -o left does, but that can't be the case, since XDMCP session starts in landscape too, and I had to use xrandr -o left just like on the host.  Interesting...

---

### Post by deadguy on 2008-06-23
I began to suspect that it was a sync issue.  Perhaps the XDMCP configuration has a different sync setting than the host configuration.  But a quick xrandr --verbose on each showed they were identical.  I tried each Hsync and Vsync, with no noticeable difference.

---

### Post by schmolch on 2008-07-15
Using the same card i have to disable dri for a fast portrait mode.


Section "Device"
	Identifier  "Videocard0"
	Driver      "intel"
	Option	    "DRI" "false"
	Option "AccelMethod" "xaa"
	#Option "MigrationHeuristic" "greedy"
	#Option "ExaNoComposite" "false"

EndSection

---

### Post by doru001 on 2011-05-26
Try this: [* Modeline Calculator]("http://www.arachnoid.com/modelines/index.html")

---

