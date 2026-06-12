---
title: "Cannot get compiz fusion to work..."
date: 2008-06-02
forum: General Help
---

### Post by JohnnyWhite2007 on 2008-06-02
Ok I tried to reinstall compiz fusion so that maybe it would work properly because some of the plugins would not enable. You click the check box, and it unclicks itself. So I uninstalled it all and tried to reinstall. Well now when I try to enable Visual effects >> extra, it says Desktop effects cannot be enabled. (They were previously enabled) Also when I type compiz I get this:

compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0

Also when I type in emerald --replace, it kinda freezes and does nothing for a long time. With compiz --replace, it says: 

compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

I dont' know why it isn't working, I can't even get emerald to work. So please if someone has an answer or solution, please help me.

Thank you in advance.

---

### Post by Forlong on 2008-06-03
Run this and post the output here: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by JohnnyWhite2007 on 2008-06-03
Well now I have it running, but now it runs really slow. The animations are running slower than what they were and loading web pages take forever now.I don't understand why it is doing this. Does anyone know why it is making everything run slower.

Oh, and the Compiz-Check command says:

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      Xgl

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Forlong on 2008-06-03
You shouldn't need Xgl on an intel chip.
Remove it:
```
sudo apt-get remove xserver-xgl
```
Then restart X and try again.

---

### Post by JohnnyWhite2007 on 2008-06-03
Ok that works. Thanks a lot. Runs like normal.... but for some reason, the Atlantis plugin doesn't want to work. This is the reason why I went through all this is to get it to work, now I am back to square one. When I click on the check box, it unclicks itself. Any ideas on this one?

---

### Post by Forlong on 2008-06-04
It seems like Ubuntu got rid of Atlantis in their packages, at least I cant find it any more on my install (it was definitely there by the time I wrote my set up guide).

---

