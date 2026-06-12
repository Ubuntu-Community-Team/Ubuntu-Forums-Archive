---
title: "[SOLVED] Switch user causes screen to blank to white"
date: 2008-04-26
forum: General Help
---

### Post by peterdm on 2008-04-26
After logging out a second user that had been switched to earlier, the logon screen blanks to an all white screen with a mouse cursor on it.
I am using a recent nvidia card with proprietary nvidia drivers, gnome and compiz fusion.
With the following scenario it is *always* reproducible:
1. Log on one user
2. Switch user and log on a second user
3. Log out the second user
4. Instead of a logon screen, the screen blanks to an all white screen with a mouse cursor.

Workaround: the logon screen is all white, but it is still functional. It is possible to blindly type the user name (followed by enter) and password (followed by enter) and the logged on session of the first user will pop up again.

I have found several posts of users reporting similar issues against different versions of ubuntu, pointing in the direction of compiz.
I've had this problem in Gutsy and now I'm still having it in Hardy.

Still I can't find a solid solution anywhere.

Does anybody have a clue about this?

Peter

---

### Post by Zorael on 2008-04-26
Does the same happen if you switch to a terminal (Ctrl+Alt+F1)? I had this happen in Feisty, but it got better if I added a whole bunch of options to my /etc/X11/xorg.conf. My X locked up though, no blind typing for me.

[quote=me]Don't mind the comments, they're remnants of where I copy/pasted the actual options from, and they're there to remind me I don't know what I'm doing.
```
...

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce Go 7600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce Go 7600]"
    Monitor        "Generic Monitor"
   	Option		"NoLogo" "true"
	Option		"NvAGP" "0" # (Only if not using an AGP card. Yours should be PCI-E I'm pretty sure)
	Option		"AddARGBGLXVisuals" "True"
	Option		"AllowGLXWithComposite" "True"
#	Option		"DisableGLXRootClipping" "True" #Just do NOT use the Option "DisableGLXRootClipping" "True". Unless you have an g86 GPU card(GF 8500-8600etc) and unfortunately have to use 100.14.11 driver...  Cause it produces blinking screen stuff, low performance, sluggish operation and sometimes lockups too.
	Option		"RenderAccel" "True"
	Option		"DamageEvents" "True"
	Option		"UseEvents" "False" # (If you face frequent lockups PLEASE set this to "False". This one causes them for sure!!)
	Option		"TripleBuffer" "True" #increases latency slightly (delay between user input and displayed result).
	Option		"BackingStore" "True" # [Use this one with caution it may NOT work on all systems (freezes when load beryl-manager) but give it a try because it helps performance] It can also break Xinerama, If you get ANY kind of strange stuff(White Windows in Compiz Fusion!) after you applied the settings remove this option and try again.
	Option		"RandRRotation" "on"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

Section "Extensions"
	Option		"DAMAGE" "Enable"
	Option		"RENDER" "Enable"
	Option		"Composite" "Enable"
EndSection
```[/quote]

---

### Post by jefferystone on 2008-04-28
peterdm,

Same issue here, yet it doesn't happen every time - seems to be resolved when I disable Desktop Effects.  I had the same issue with 7.10 as I do with 8.04.

Hopefully there will be a fix.

Had to disable Desktop Effects amyway for an issue with OpenGL/Fullscreen going to windowed mode.

Sincerely,

Jeffery Stone

---

### Post by halln on 2008-04-29
right click the user switcher icon then untick lock screen. Simple as that.

---

### Post by fs3rp4 on 2008-04-29
> **peterdm said:**
> After logging out a second user that had been switched to earlier, the logon screen blanks to an all white screen with a mouse cursor on it.
I am using a recent nvidia card with proprietary nvidia drivers, gnome and compiz fusion.
With the following scenario it is *always* reproducible:
1. Log on one user
2. Switch user and log on a second user
3. Log out the second user
4. Instead of a logon screen, the screen blanks to an all white screen with a mouse cursor.

Workaround: the logon screen is all white, but it is still functional. It is possible to blindly type the user name (followed by enter) and password (followed by enter) and the logged on session of the first user will pop up again.

I have found several posts of users reporting similar issues against different versions of ubuntu, pointing in the direction of compiz.
I've had this problem in Gutsy and now I'm still having it in Hardy.

Still I can't find a solid solution anywhere.

Does anybody have a clue about this?

Peter



This is a old problem from Nvidia proprieraty drivers and compiz. The only solution is disable compiz if you have to switch users...

---

### Post by zoiks on 2008-05-13
> **fs3rp4 said:**
> This is a old problem from Nvidia proprieraty drivers and compiz. The only solution is disable compiz if you have to switch users...

I'm having precisely the same problem as peterdm, sad to hear there's no fix for this yet.

---

### Post by peterdm on 2008-07-07
This issue is fixed in Hardy (in my case at least).

---

