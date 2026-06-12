---
title: "Beryl help requested"
date: 2007-01-02
forum: General Help
---

### Post by nickoli on 2007-01-02
I get the following error message when I fire up beryl;

 XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Initiating splash
beryl: water: GL_ARB_fragment_program is missing

I modified my xorg.conf file like this

Section "Device"
Identifier "Intel Corporation Intel Default Card"
Driver "ati"
Option "XAANoOffscreenPixmaps"
BusID "PCI:0:2:0&#8243;
EndSection

plus I did the other modifications listed on the beryl wiki. I was wondering if I need to make more mods. I'm really curious how to get the cube , beryl seems to be functioning. Which is cool cause the last time I tried it I could'nt even get that to happen. Any help will be appreciated.

---

### Post by Waappu on 2007-01-03
Hi

Disable water plug in from Beryl setting manager. Your video card or drivers do not support the rendering of the water effects. Other wise it should be ok.

You can see this thread about same problem
[http://ubuntuforums.org/showthread.php?t=328205&highlight=water%3A+GL_ARB_fragment_program+is+missing](http://ubuntuforums.org/showthread.php?t=328205&highlight=water%3A+GL_ARB_fragment_program+is+missing)

---

### Post by fokuslee on 2007-01-03
OMG i want the cube too
i can't get the cube for some reason i never see the top and bottom when rotating, i assume this is some kinda of setup option
but still if you get it to show the full cube plz let me know
thanks buddy

---

### Post by nickoli on 2007-01-03
Yea, thanks  that resolves that error, now if I could only get that wonderful cube.

---

### Post by Waappu on 2007-01-03
Hi

Do you have Desktop plug in enabled? Check also from notify area Beryl icon that Beryl window manager and Emerald decorator are selected.

---

### Post by Waappu on 2007-01-03
Hi

This might help also for Beryl settings
[My settings are all messed up and I can't start the settings manager, how can I fix this?]("http://www.beryl-project.org/faq.php#uq8")

[http://wiki.beryl-project.org/index.php/Plugins/PluginOptions](http://wiki.beryl-project.org/index.php/Plugins/PluginOptions)

---

### Post by Waappu on 2007-01-03
Hi

Or this
[http://www.ubuntuforums.org/showthread.php?t=320790&highlight=beryl+plugin+settings](http://www.ubuntuforums.org/showthread.php?t=320790&highlight=beryl+plugin+settings)

[http://www.ubuntuforums.org/showthread.php?t=301895&highlight=beryl+plugin+settings](http://www.ubuntuforums.org/showthread.php?t=301895&highlight=beryl+plugin+settings)

---

### Post by Waappu on 2007-01-03
And here is default commands
[http://wiki.beryl-project.org/wiki/Tips/Default_Commands](http://wiki.beryl-project.org/wiki/Tips/Default_Commands)

---

### Post by fokuslee on 2007-01-03
hellyeah waappu is the man!!!!!
ctrl alt +left click does the trick sweeeeetness

ps we should post our screens it would be nice

---

### Post by Waappu on 2007-01-03
Hi

I'm clad that you get it working =)
I found this thread for screenshots
[http://ubuntuforums.org/showthread.php?t=330302](http://ubuntuforums.org/showthread.php?t=330302)

---

