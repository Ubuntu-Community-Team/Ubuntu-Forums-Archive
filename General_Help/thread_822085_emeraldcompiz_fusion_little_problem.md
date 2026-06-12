---
title: "emerald/compiz fusion little problem"
date: 2008-06-07
forum: General Help
---

### Post by Piteco on 2008-06-07
I've benn using compiz fusion without problems since I installed hardy. Today I took a emerald theme for the fisrt time, selected it at emerald and ran "emerald --replace" in the terminal and POOF! theres was no more window decoration, all the top-right buttoms had gone.And when i open the compiz fusion manager, all the options are unmarked. how can i have my buttoms back?

---

### Post by cubeist on 2008-06-07
I think there is a plugin in CCSM called window decorator (or something like that).  Make sure that is checked.  I think you can also specify which window decorator you want in that plugin...(sorry can't be more helpful, no compiz on this comp at the moment!)

---

### Post by Piteco on 2008-06-07
Doesn't work, I've already tried it.

---

### Post by Forlong on 2008-06-08
What happens when running
```
gtk-window-decorator --replace
``` in the terminal?

---

### Post by Piteco on 2008-06-08
nothing happens

---

### Post by Forlong on 2008-06-08
Is Compiz running at all?

What's the output when running ```
compiz
``` in a terminal?

---

### Post by Piteco on 2008-06-08
```
lucas@lucas-desktop:~$ compiz
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0

lucas@lucas-desktop:~$ compiz --replace

```
after running it, the windows decoration disappears and I deactivate the desktop effects to get it back

---

### Post by Grishka on 2008-06-08
use fusion-icon. it takes care of many problems of that kind.

---

### Post by Forlong on 2008-06-08
Piteco, what's the output of ```
dpkg -l | grep compiz
```

---

### Post by Piteco on 2008-06-08
```
ii  compiz                                     1:0.7.4-0ubuntu6                    OpenGL window and compositing manager
ii  compiz-core                                1:0.7.4-0ubuntu6                    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.7.4-0ubuntu1                      Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.7.4-0ubuntu5                      Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.7.4-0ubuntu6                    OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.7.4-0ubuntu6                    OpenGL window and compositing manager - plug
ii  compizconfig-backend-gconf                 0.7.4-0ubuntu1                      Settings library for plugins - OpenCompositi
rc  compizconfig-settings-manager              0.7.4-0ubuntu2                      Compiz configuration settings manager
rc  emerald                                    0.7.2-0ubuntu2                      Decorator for compiz-fusion
ii  libcompizconfig0                           0.7.4-0ubuntu1                      Settings library for plugins - OpenCompositi
rc  libemeraldengine0                          0.7.2-0ubuntu2                      Decoration engines for compiz-fusion

```

---

### Post by Forlong on 2008-06-09
And the output of ```
ls -l /usr/bin/compiz
```

---

### Post by mikey.duhhh on 2008-06-09
I have the same problem and it seems nothing is helping.  I even tried uninstalling Emerald and still had the same problem, no top bar, no buttons. Re-installing it gave me a randomly colored bar at top (with no buttons) sometimes.  At other times it is clear.

---

### Post by Piteco on 2008-06-09
-rwxr-xr-x 1 root root 10129 2008-04-21 17:27[COLOR="Lime"] /usr/bin/compiz
[/COLOR]

---

### Post by Forlong on 2008-06-09
Everything seems to be OK so far.

What's the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by Piteco on 2008-06-09
```

lucas@lucas-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV44A [GeForce 6200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Could not check the amount of memory on your Nvidia chip. 

Would you like to know more? (Y/n) y

 That does not mean, you will not be able to use Compiz.
 If everything else went OK you are most probably fine.

 In case you want the script to check this step as well, install the program
 nvidia-settings on your system.

```

---

### Post by Piteco on 2008-06-12
I've installed the nvidia-settings and evrething is ok at compz-check, but my window decoration still desapearing

---

