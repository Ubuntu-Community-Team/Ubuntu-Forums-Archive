---
title: "compiz missing menu"
date: 2008-05-05
forum: General Help
---

### Post by 565Customz on 2008-05-05
im missing the menu that is supposed to be in the upper right panel. that allows you to basically control compiz.. i purged it and reinstalled it along with the ccsm and it still isnt working...
 
anyone?

---

### Post by isaacj87 on 2008-05-05
Are you referring to the fusion-icon? Try doing a "sudo apt-get install fusion-icon"

---

### Post by 565Customz on 2008-05-05
slider@8uTt3r:~$ sudo apt-get install fusion-icon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fusion-icon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fusion-icon (0.0.0+git20071028-2ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing fusion-icon (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 fusion-icon
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by 565Customz on 2008-05-05
which is weird cuz i just formatted this computer and did a fresh install...also installed all the compiz plugins as well but i dont think they are causing this...this all works fine on my laptop

---

### Post by isaacj87 on 2008-05-05
hmm...That's weird...maybe a corrupted download?

Do me a favor (cause I really don't have any clue)...try this:

```
sudo apt-get install python-compizconfig
```

Then try installing fusion-icon again.

---

### Post by 565Customz on 2008-05-05
slider@8uTt3r:~$ sudo apt-get install python-compizconfig
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-compizconfig is already the newest version.
python-compizconfig set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fusion-icon (0.0.0+git20071028-2ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing fusion-icon (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 fusion-icon
E: Sub-process /usr/bin/dpkg returned an error code (1)



something is wrong with fusion...

its installed and in the system tools menu...i just dont have any management ability with it...i dont know whats up

---

### Post by 565Customz on 2008-05-05
get this error when tryin to reinstall from synaptic

E: fusion-icon: subprocess post-installation script returned error exit status 1

---

### Post by isaacj87 on 2008-05-05
Uhhh...

Try this? 

```
sudo dpkg --configure -a
```

Does that do the trick?

or maybe...

```
sudo apt-get install -f
```

---

### Post by 565Customz on 2008-05-05
slider@8uTt3r:~$ sudo dpkg --configure -a
Setting up fusion-icon (0.0.0+git20071028-2ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing fusion-icon (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 fusion-icon

---

### Post by 565Customz on 2008-05-05
lider@8uTt3r:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fusion-icon (0.0.0+git20071028-2ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing fusion-icon (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 fusion-icon
E: Sub-process /usr/bin/dpkg returned an error code (1)


hmmmm now what...lol...i think im gonna format it again and start over

---

### Post by isaacj87 on 2008-05-05
Before you re-format!

Okay let's start over...

First remove fusion-icon

```
sudo apt-get remove fusion-icon
```

now run:

```
sudo apt-get clean
```

Then reinstall fusion-icon...does that do the trick? It may just be a corrupted download

---

### Post by 565Customz on 2008-05-05
i think we are on the right track with that dpkg file...whatever that is..anyway i can swap it for a known good version?

---

### Post by 565Customz on 2008-05-05
got a crash report...when i ran fusion-icon in terminal...seemed to install fine though

---

### Post by 565Customz on 2008-05-05
hey maybe ive got the wrong repository and i keep installing a bad file...how do we check.change that?

---

### Post by 565Customz on 2008-05-05
tried doing a deb file i found and it does the same thing...it just wont load up ....i dont get it

---

### Post by isaacj87 on 2008-05-05
Run fusion-icon in Terminal and post the output. I want to see what it's saying.

---

### Post by 565Customz on 2008-05-05
slider@8uTt3r:~$ fusion-icon &
[1] 6203
slider@8uTt3r:~$  * Detected Session: gnome
 * Searching for installed applications...
Backend     : gconf
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
 * Intel detected, exporting: INTEL_BATCH=1
 * Using the GTK Interface
 * Starting Compiz
 ... executing: compiz --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering
Backend     : gconf
Integration : true
Profile     : default
Adding plugin screensaver (screensaver)
Adding plugin anaglyph (anaglyph)
Adding plugin wallpaper (wallpaper)
Adding plugin loginout (loginout)
Adding plugin workspacenames (workspacenames)
Adding plugin atlantis (atlantis)
Adding plugin freewins (freewins)
Adding plugin photo (photo)
Adding plugin snowglobe (snowglobe)
Adding plugin colorfilter (colorfilter)
Adding plugin snow (snow)
Adding plugin addhelper (addhelper)
Adding plugin cubecaps (cubecaps)
Adding plugin animation (animation)
Adding plugin shift (shift)
Adding plugin firepaint (firepaint)
Adding plugin annotate (annotate)
Adding plugin imgjpeg (imgjpeg)
Adding plugin water (water)
Adding plugin widget (widget)
Adding plugin splash (splash)
Adding plugin zoom (zoom)
Adding plugin fs (fs)
Adding plugin inotify (inotify)
Adding plugin group (group)
Adding plugin snap (snap)
Adding plugin gears (gears)
Adding plugin screenshot (screenshot)
Adding plugin showdesktop (showdesktop)
Adding plugin png (png)
Adding plugin workarounds (workarounds)
Adding plugin thumbnail (thumbnail)
Adding plugin vpswitch (vpswitch)
Adding core settings (General Options)
Adding plugin ring (ring)
Adding plugin scaleaddon (scaleaddon)
Adding plugin expo (expo)
Adding plugin resizeinfo (resizeinfo)
Adding plugin cube (cube)
Adding plugin maximumize (maximumize)
Adding plugin text (text)
Adding plugin mousepoll (mousepoll)
Adding plugin clone (clone)
Adding plugin move (move)
Adding plugin 3d (3d)
Adding plugin regex (regex)
Adding plugin scalefilter (scalefilter)
Adding plugin glib (glib)
Adding plugin rotate (rotate)
Adding plugin blur (blur)
Adding plugin minimize (minimize)
Adding plugin mswitch (mswitch)
Adding plugin dbus (dbus)
Adding plugin mblur (mblur)
Adding plugin place (place)
Adding plugin bench (bench)
Adding plugin scale (scale)
Adding plugin bs (bs)
Adding plugin fade (fade)
Adding plugin put (put)
Adding plugin trailfocus (trailfocus)
Adding plugin resize (resize)
Adding plugin svg (svg)
Adding plugin opacify (opacify)
Adding plugin fadedesktop (fadedesktop)
Adding plugin bicubic (bicubic)
Adding plugin mag (mag)
Adding plugin wall (wall)
Adding plugin neg (neg)
Adding plugin ezoom (ezoom)
Adding plugin video (video)
Adding plugin extrawm (extrawm)
Adding plugin reflex (reflex)
Adding plugin crashhandler (crashhandler)
Adding plugin notification (notification)
Adding plugin tile (tile)
Adding plugin cubeaddon (cubeaddon)
Adding plugin session (session)
Adding plugin decoration (decoration)
Adding plugin fakeargb (fakeargb)
Adding plugin wobbly (wobbly)
Adding plugin switcher (switcher)
Adding plugin winrules (winrules)
Adding plugin showmouse (showmouse)
Adding plugin shelf (shelf)
Initializing core options...done
Initializing imgjpeg options...done
Initializing workarounds options...done
Initializing vpswitch options...done
Initializing text options...done
Initializing move options...done
Initializing place options...done
Initializing resize options...done
Initializing svg options...done
Initializing neg options...done
compiz (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Initializing video options...done
Initializing extrawm options...done
Initializing session options...done
Initializing decoration options...done
Initializing wobbly options...done
Initializing animation options...done
Initializing shift options...done
Initializing snap options...done
Initializing resizeinfo options...done
Initializing fade options...done
Initializing cube options...done
Initializing 3d options...done
Initializing rotate options...done
Initializing scale options...done
**GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.**
Initializing scaleaddon options...done
Initializing expo options...done
Initializing ezoom options...done
Initializing switcher options...done
Setting Update "shadow_radius"
Setting Update "command"
Setting Update "close_effects"
Setting Update "close_durations"
Setting Update "fire_color"
Setting Update "resistance_distance"
Setting Update "attraction_distance"
Setting Update "fullscreen_visual_bell"



you see that error i highlighted? thats new it hasnt made it that far yet lol

---

### Post by tab10 on 2008-05-05
I think you mean CCSM you should try to input that in console. And read what it says. I had the same thing and then i remembered the name of it. After I just inputted that in Console it basically gave me the command to install it :guitar: 

That should solve it HF

---

### Post by 565Customz on 2008-05-05
all that does is start ccsm

---

### Post by tab10 on 2008-05-05
Then I don't get which menu your referring to. I control my compiz with CCSM

---

### Post by 565Customz on 2008-05-05
fusion icon controls ccsm

---

### Post by 565Customz on 2008-05-05
or should i say...it controls you windows managers

---

### Post by isaacj87 on 2008-05-05
From what I can tell, fusion-icon is starting up fine. There isn't an error (that i can see at least)...

About the highlighted part...It's referring to a bad value for the scale plugin. Go into CCSM, go to the Scale plugin and under the "Bindings" tab...where it says "Initiate Window Picker" click the little trash can icon on the right side and reset the value.

---

### Post by Zorael on 2008-05-05
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
fusion-icon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fusion-icon (0.0.0+git20071028-2ubuntu2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing fusion-icon (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
fusion-icon
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Though perhaps not relevant at this point, this should help the above crux.
```
$ sudo dpkg --purge fusion-icon
$ sudo aptitude install fusion-icon
```

---

