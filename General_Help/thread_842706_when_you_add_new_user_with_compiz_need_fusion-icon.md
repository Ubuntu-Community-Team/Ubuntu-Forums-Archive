---
title: "when you add new user with compiz need fusion-icon"
date: 2008-06-27
forum: General Help
---

### Post by sdowney717 on 2008-06-27
Not sure why. I added a new user and compiz had problems starting with the new user.
So I discovered if I run fusion-icon, then compiz starts up fine. So I put fusion-icon in the sessions startup.
Any ideas or is this normal.

---

### Post by Forlong on 2008-06-27
A couple o' more info would be nice.

Run this as your new user and post the output here: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by sdowney717 on 2008-06-27
tricia@scott-desktop:~/Desktop$ ./compiz-chec

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

tricia@scott-desktop:~/Desktop$

---

### Post by sdowney717 on 2008-06-27
I some time ago may have installed the latest and greatest compiz?
If I ran just compiz --replace I would get errors
but run fusion-icon all is well
And I get the little blue fusion icon in the panel.

```

tricia@scott-desktop:~/Desktop$ compiz --replace
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
tricia@scott-desktop:~/Desktop$ fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
Backend     : gconf
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
 * No GLX_EXT_texture_from_pixmap with direct rendering context
 ... present with indirect rendering, exporting: LIBGL_ALWAYS_INDIRECT=1
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
Backend     : gconf
Integration : true
Profile     : default
Adding plugin maximumize (maximumize)
Adding plugin wallpaper (wallpaper)
Adding plugin decoration (decoration)
Adding plugin switcher (switcher)
Adding plugin blur (blur)
Adding plugin text (text)
Adding plugin screenshot (screenshot)
Adding plugin showdesktop (showdesktop)
Adding plugin snowglobe (snowglobe)
Adding plugin rotate (rotate)
Adding plugin ring (ring)
Adding plugin water (water)
Adding plugin wall (wall)
Adding plugin atlantis (atlantis)
Adding plugin annotate (annotate)
Adding plugin tile (tile)
Adding plugin workarounds (workarounds)
Adding plugin resize (resize)
Adding plugin snow (snow)
Adding plugin cubeaddon (cubeaddon)
Adding plugin session (session)
Adding plugin extrawm (extrawm)
Adding plugin vpswitch (vpswitch)
Adding plugin inotify (inotify)
Adding plugin mag (mag)
Adding plugin winrules (winrules)
Adding plugin staticswitcher (staticswitcher)
Adding plugin freewins (freewins)
Adding plugin mousepoll (mousepoll)
Adding plugin opacify (opacify)
Adding plugin clone (clone)
Adding plugin scale (scale)
Adding plugin dbus (dbus)
Adding plugin addhelper (addhelper)
Adding plugin fakeargb (fakeargb)
Adding plugin resizeinfo (resizeinfo)
Adding plugin cube (cube)
Adding plugin bench (bench)
Adding plugin screensaver (screensaver)
Adding plugin bs (bs)
Adding plugin group (group)
Adding plugin scalefilter (scalefilter)
Adding plugin video (video)
Adding plugin 3d (3d)
Adding plugin reflex (reflex)
Adding plugin thumbnail (thumbnail)
Adding plugin colorfilter (colorfilter)
Adding plugin gears (gears)
Adding plugin notification (notification)
Adding plugin showmouse (showmouse)
Adding plugin mswitch (mswitch)
Adding plugin anaglyph (anaglyph)
Adding plugin widget (widget)
Adding plugin scaleaddon (scaleaddon)
Adding plugin shelf (shelf)
Adding plugin move (move)
Adding plugin place (place)
Adding plugin loginout (loginout)
Adding plugin bicubic (bicubic)
Adding plugin trailfocus (trailfocus)
Adding plugin splash (splash)
Adding plugin imgjpeg (imgjpeg)
Adding plugin crashhandler (crashhandler)
Adding plugin snap (snap)
Adding plugin svg (svg)
Adding plugin fs (fs)
Adding plugin fadedesktop (fadedesktop)
Adding plugin minimize (minimize)
Adding plugin photo (photo)
Adding plugin neg (neg)
Adding plugin png (png)
Adding plugin mblur (mblur)
Adding plugin animation (animation)
Adding plugin put (put)
Adding plugin dodge (dodge)
Adding plugin zoom (zoom)
Adding plugin expo (expo)
Adding plugin workspacenames (workspacenames)
Adding plugin fade (fade)
Adding plugin glib (glib)
Adding plugin regex (regex)
Adding plugin wobbly (wobbly)
Adding plugin ezoom (ezoom)
Adding plugin shift (shift)
Adding plugin firepaint (firepaint)
Adding core settings (General Options)
Initializing core options...done
Initializing text options...done
Initializing workarounds options...done
Initializing resize options...done
Initializing session options...done
Initializing extrawm options...done
Initializing vpswitch options...done
Initializing resizeinfo options...done
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing move options...done
Initializing place options...done
Initializing imgjpeg options...done
Initializing svg options...done
Initializing neg options...done
Initializing shift options...done
Initializing decoration options...done
Initializing wall options...done
Initializing snap options...done
Initializing animation options...done
Initializing wobbly options...done
Initializing expo options...done
Initializing fade options...done
Initializing switcher options...done
Initializing scale options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing scaleaddon options...done
Setting Update "shadow_radius"
Setting Update "command"
Setting Update "fullscreen_visual_bell"




```

---

### Post by Forlong on 2008-06-27
> **sdowney717 said:**
> I some time ago may have installed the latest and greatest compiz?
May have?
What's the output of ```
ls -l $(command -v compiz)
```

---

### Post by sdowney717 on 2008-06-27
tricia@scott-desktop:~$ ls -l $(command -v compiz)
-rwxr-xr-x 1 root root 938524 2008-06-11 14:37 /usr/local/bin/compiz
tricia@scott-desktop:~$

---

### Post by Forlong on 2008-06-28
So you did compile Compiz from source.
Then that's normal.
In Ubuntu, what you start with 'compiz' is not Compiz itself but a script to start it properly.
Since you compiled Compiz yourself, 'compiz' is now the actual binary. This one requires you to start it with certain options.
That's what the script is there for -- but Fusion-Icon does the same thing.

If you are fine with Fusion-Icon then use it for all users. If you'd like too avoid it (what I can understand), let me know. We'll find a way to make it work without it.

---

