---
title: "Fontforge runs but does not display, Unity 14.04"
date: 2014-12-26
forum: General Help
---

### Post by Xiguus on 2014-12-26
Hi All,
I am running 14.04 with Unity and have installed FontForge from the repositories, version 20141126-0ubuntu1~trusty. When I run the program the splash screen and file selector show but after selecting a font the program appears to stall, ie no user windows appear. An icon is put in the Launcher with the little 'active' marks and the Task Swapper also shows an icon, but I cannot swap to a visible window with either of these. The program does not appear in the top listing and I cannot shut it down.  Does anyone know what is going on here?
Thanx in advance...

---

### Post by CantankRus on 2014-12-26
No problem here.(trusty 14.04)
Try running **fontforge** in terminal to see errors.
eg
```
fontforge [COLOR="#FF0000"]**/path/to/fontfile**[/COLOR]
```
Use [COLOR="#FF0000"]**your path**[/COLOR].

Synaptic shows mine to be a different version than yours.
Have you added any 3rd party ppas?

---

### Post by Xiguus on 2014-12-28
Hi CantankRus,

Thxs for your reply.
Re version, yes, I installed this version from launchpad after the synaptic package failed in similar manner.
PPA is [http://ppa.launchpad.net/fontforge/fontforge/ubuntu](http://ppa.launchpad.net/fontforge/fontforge/ubuntu) trusty main
Running the program as you suggest I get
```

$ fontforge /usr/share/fonts/type1/gsfonts/a010015l.pbf
Copyright (c) 2000-2014 by George Williams. See AUTHORS for Contributors.
 License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
 with many parts BSD <http://fontforge.org/license.html>. Please read LICENSE.
 Based on sources from 00:59 UTC 27-Nov-2014-ML-D.
 Based on source from git with hash: c4cea471798c92848170c2f47311979805966093
Failed to open hotkey definition file: /usr/share/fontforge/hotkeys/default
no xdefs_filename!
TESTING: getPixmapDir:/usr/share/fontforge/pixmaps
TESTING: getShareDir:/usr/share/fontforge
TESTING: GResourceProgramDir:/usr/bin
trying default theme:/usr/share/fontforge/pixmaps/resources
else argv[i]:/usr/share/fonts/type1/gsfonts/a010015l.pfb
SplineFontPieceMeal() going unhinted...

```
which is where the program hangs. As stated above, there is an icon in the launcher and another in the task switcher.
Hope this helps...
BR ;)

---

### Post by CantankRus on 2014-12-28
Fontforge from the the default repositories opens without error and I can select a font from the dialogue window.
Fontforge from the fontforge ppa opens with the same errors as you but I can still load the font.

There is no such font as what you tried to load.
The extension is .**[COLOR="#FF0000"]pfb[/COLOR]** not .pbf but in any case you should still see an error window if the file doesn't exist.
eg
```
fontforge '/usr/share/fonts/type1/gsfonts/a010015l.[COLOR="#FF0000"]**pfb**[/COLOR]'
```

If you still don't get an "open font" window, test fontforge in your guest account
or in another desktop environment if installed.

**P.S.** Had a brief look at some of your previous posts.
Is this the same upgraded install or is it a fresh 14.04 install?

---

### Post by Xiguus on 2014-12-28
Hi CantankRus,

Thxs for your prompt response.
Ubuntu 14.04 is a new installation into an empty partition.
Test file I loaded was pfb, as seen for 'argv' above - pbf in the command line is a typo, code output is cut-and-paste from terminal.
I've also tested with a couple of other fonts, eg ttf, using the command line and the Dash launcher. In the latter case I get the splash screen and a file-open dialogue, and can see a progress bar, but the font window does not appear. Results are consistent for all font types.
When using the command line my terminal looks just like yours, difference is I don't have a visible window on the desktop. 
Regardless of how I launch the program, the Task Switcher shows both a fontforge font display window and the warnings window, but selecting either of these does not result in the window being displayed.
Behaviour is identical in the 'Guest' account.
Hope this clarifies the present state of affairs...
BR ;).

---

### Post by CantankRus on 2014-12-28
Strange....
I've installed a lot of stuff so booted to a live trusty iso, installed fontforge
and worked no problem.
:confused:

---

