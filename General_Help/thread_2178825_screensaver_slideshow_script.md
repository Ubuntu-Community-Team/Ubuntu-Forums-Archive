---
title: "screensaver slideshow script"
date: 2013-10-05
forum: General Help
---

### Post by linuxandunix on 2013-10-05
I need help in creating a small script which will run the screensaver(either xscreensaver or gnome-screensaver) to run a slideshow of images from a particular location. I'm using Ubuntu 12.04LTS 64bit.

---

### Post by raja.genupula on 2013-10-05
are you sure that you want only script because we have some applications which can do that what do you want.

Thank you.

---

### Post by ajgreeny on 2013-10-05
Xscreensaver can already produce a slideshow of images from any folder on your computer; I already use it for just that and change the folder I use regularly; why reinvent the wheel?

Make sure you have the xscreensaver-gl installed and it will be in the long list of screensavers available.

Xscreensaver is a much better option that gnome-screensaver in my opinion, as it is a lot more flexible and configurable.

---

### Post by linuxandunix on 2013-10-06
I manage a couple of ubuntu systems through Puppet. I need to deploy  a script so that a pre-defined set of pictures will display as slideshow when screensaver is activated.

---

### Post by ajgreeny on 2013-10-07
If you use xscreensaver there will be a hidden .xscreensaver file in the users home of each machine which you could edit remotely by script to change anything you wanted.  Here is mine with the long list of screensavers which are available on my machine edited out, but the slideshow line still there.  This may give you some clues as to how to proceed with this remote configuration.
```

# XScreenSaver Preferences File
# Written by xscreensaver-demo 5.15 for username on Fri May 17 17:34:54 2013.
# http://www.jwz.org/xscreensaver/

timeout:    0:08:00
cycle:        0:00:00
lock:        False
lockTimeout:    0:00:00
passwdTimeout:    0:00:30
visualID:    default
installColormap:    True
verbose:    False
timestamp:    True
splash:        True
splashDuration:    0:00:05
demoCommand:    xscreensaver-demo
prefsCommand:    xscreensaver-demo -prefs
nice:        10
memoryLimit:    0
fade:        True
unfade:        False
fadeSeconds:    0:00:03
fadeTicks:    20
captureStderr:    True
ignoreUninstalledPrograms:False
font:        *-medium-r-*-140-*-m-*
dpmsEnabled:    True
dpmsQuickOff:    False
dpmsStandby:    0:30:00
dpmsSuspend:    0:30:00
dpmsOff:    1:00:00
grabDesktopImages:  False
grabVideoFrames:    False
chooseRandomImages: True
imageDirectory:    /home/username/Pictures/Family/Venture

mode:        one
selected:    142

textMode:    url
textLiteral:    XScreenSaver
textFile:    
textProgram:    fortune
textURL:    http://fridge.ubuntu.com/node/feed

programs:                                      \
LIST EDITED OUT

  GL:                 glslideshow -root -duration 20 -zoom 50          \
                  -pan 20 -fade 3                \n\

LIST EDITED OUT

pointerPollTime:    0:00:05
pointerHysteresis:  10
windowCreationTimeout:0:00:30
initialDelay:    0:00:00
GetViewPortIsFullOfLies:False
procInterrupts:    True
xinputExtensionDev: False
overlayStderr:    True
```

---

### Post by linuxandunix on 2013-10-15
Thanks [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747"). It solved my problem.

---

