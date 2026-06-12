---
title: "Compiz Fusion"
date: 2008-04-28
forum: General Help
---

### Post by Shadius on 2008-04-28
Okay, I'm a total noob to Ubuntu so I need help. Hopefully I came to the right place. Okay, so I've seen all these things about Compiz Fusion, and all these crazy effects, but how do I get it? I'm sure I can figure out how to use it once I get it, but I don't know where to go to get it? Could you point me in the right direction?

---

### Post by alsamman on 2008-04-28
> **Shadius said:**
> Okay, I'm a total noob to Ubuntu so I need help. Hopefully I came to the right place. Okay, so I've seen all these things about Compiz Fusion, and all these crazy effects, but how do I get it? I'm sure I can figure out how to use it once I get it, but I don't know where to go to get it? Could you point me in the right direction?

open up terminal and type this
```
 sudo apt-get install ccsm 
```

then once that is done installing go to System>Preferences>Advanced Desktop Settings and that is where u can customize compiz
Edit: Compiz is already installed by default on Ubuntu so what you are installing is just a manager that you can customize what effects you want etc.

---

### Post by Shadius on 2008-04-28
Okay, thanks. Just so I know, what's ccsm?

---

### Post by alsamman on 2008-04-28
> **Shadius said:**
> Okay, thanks. Just so I know, what's ccsm?

Compiz Configuration Settings Manager

---

### Post by Shadius on 2008-04-28
Oh okay, thank you.

---

### Post by Shadius on 2008-04-28
It says couldn't find package ccsm.

---

### Post by alsamman on 2008-04-28
> **Shadius said:**
> It says couldn't find package ccsm.

lmao thats my fault the actual name of the package is
```

sudo apt-get install compizconfig-settings-manager
```

---

### Post by Shadius on 2008-04-28
Oh. LoL. Thanks. Okay, once this is installed I'll be able to use Fire, Cube, etc...??

---

### Post by alsamman on 2008-04-28
> **Shadius said:**
> Oh. LoL. Thanks. Okay, once this is installed I'll be able to use Fire, Cube, etc...??

as long as u have your graphics card driver installed and enabled. Compiz is believe is on by default but if you want to use it often then I recommend getting the tray icon:
```
 sudo apt-get install fusion-icon 
``` then you can use it to turn compiz on/off whenever you want and to have this tray icon load on startup, go to System>Preferences>Sessions>Add: Name: Compiz Tray Icon Command: fusion-icon

---

### Post by Shadius on 2008-04-28
Okay, did that, so now how do I see the Cube or the Fire, Water, and all the other effects??

---

### Post by bikeboy on 2008-04-28
System > Prefs > Advanced Desktop Effects Settings should give you the options. Or, you could have just gone to System > Prefs > Appearance > Visual Effects > Extra. You wouldn't have as much control, but it's a good place to start.

---

### Post by Nebutron on 2008-04-28
> **Shadius said:**
> Okay, did that, so now how do I see the Cube or the Fire, Water, and all the other effects??

When you go to system>prefernces>advanced Desktop Effects, be sure to click on GENERAL OPTIONS> DESKTOP SIZE> and set Horizontal Virtual Size to 4. You will also want to check the box next to DESKTOP CUBE and ROTATE CUBE an whatever other effects you want to enable. It's a lot of fun.  Enjoy

---

### Post by alsamman on 2008-04-28
> **Shadius said:**
> Okay, did that, so now how do I see the Cube or the Fire, Water, and all the other effects??

When you go to system-pref-advanced desktop effects settings
Cube:
Enable Desktop Cube and Rotate Cube. You "cube" will look like a flat square at first so to make it have 4 sides you to General Options, desktop size, and increase horizontal size to 4 (3- triangle 5-pentagon etc.)

Fire:
Under Animations you can make it appear when you close or minimize by editing the effect and selecting Burn

Water:
Enable Water Effect and when you click to see its settings, itll show you the bindings that initiate it (by default is it ctrl+super (super button is button with windows logo on it inbetween ctrl and alt)

---

### Post by Shadius on 2008-05-04
I enabled Desktop Cube and Rotate Cube, but I'm only getting flat panels, like a slideslow type thing. I set the desktop size to 4 already, but still no cube. Help?

---

### Post by gtrtx on 2008-05-04
It's sounds like you have expo or desktop wall enabled. You need the cube enabled. It's in the compiz settings manager. You need to look around in there to adjust the setting to your liking

---

### Post by Zorael on 2008-05-04
And do note that you want number of desktops set to 1 and horizontal size set to 4 to get a cube.

---

