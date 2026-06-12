---
title: "Testing 3d Acceleration"
date: 2007-02-11
forum: General Help
---

### Post by nomad00 on 2007-02-11
Greetings!

Could anyone tell me how to check if 3d Acceleration is fully working?

fglrxinfo & glxinfo are both returning positive results, but for some reason my screen savers run incredibly choppy.....am i missing something?

---

### Post by Ramses de Norre on 2007-02-11
Are you running AIGLX or something? Have you got a decent videocard? (Most of those GL screensavers are pretty demanding).
If glxinfo tells you direct rendering is enabled you can be pretty sure if it..

One last thing if you're on edgy and not using AIGLX or any other compositing depending tool  (no xcompmgr or something): Add this to your /etc/X11/xorg.conf file: ```
Section "Extensions"
        Option      "Composite" "0"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

```

---

### Post by nomad00 on 2007-02-11
Sorry for being so vague....i'm in 6.10 running a Radeon 9600.

[INDENT]fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.6286 (8.33.6)
[/INDENT]

[INDENT]
 glxinfo | grep direct
direct rendering: Yes[/INDENT]

xorg.conf has:
[INDENT]Section "ServerFlags"
	Option	    "AIGLX" "off"
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection[/INDENT]

I'm really confused, i'm not sure why the GL screensavers wouldn't be smooth...

---

### Post by Ramses de Norre on 2007-02-11
The following tool isn't really a correct benchmark tool but it does give an idea, run it with no other graphical tools open: ```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

I get like 250 fps on an X600 with fglrx 7.1.0-8.28.8 (repo version).

---

