---
title: "Cube Effect - How?"
date: 2007-06-20
forum: General Help
---

### Post by The Wisedude on 2007-06-20
Well I've seen some screenshots of people taking were their whole desktop is in a cube,

How do you get this?

---

### Post by michaelzap on 2007-06-20
Just install Beryl and turn on the Desktop Cube effect.

---

### Post by dfreer on 2007-06-20
Beryl/compiz/desktop effects.

Basically, it's beta software, which means it isn't guranteed to work. But you can try it out. You'll need to have 3D acceleration/direct rendering enabled for your video card, and AIGLX or XGL.

XGL requires a seperate login session generally, and you cannot do 3D gaming when using XGL AFAIK.
AIGLX is intergrated with your normal x session, so you don't need to logout/login each time to use it, and you can play 3D games with the effects enabled.

AIGLX works pretty well with most nvidia cards + intel cards, and some ATI cards that use the "Radeon" driver.
XGL generally is required for ATI cards that need the "fglrx" driver.

ok, now that I've scared you off, on my nvidia system it takes just three steps to use beryl:
System > Adminstration > Restricted Drivers Manager  (to install nvidia drivers with one click)
Applications > Accessories > Terminal:
```
sudo apt-get install beryl emerald-themes beryl-manager
beryl-manager
```

---

### Post by fjf on 2007-06-20
...and once you've done that, hold both mouse buttons and move the cube!  (took me a while to learn this one!!  ;)  )

---

### Post by The Wisedude on 2007-06-20
Ok I installed beryl now how do i Actually GO into the cube. Im in (Manager) Desktop > Desktop Cube 

??

---

### Post by steve-shinn on 2007-06-20
Have you got the red beryl emblem showing on your top  task bar ?? if so, right click on it and go to beryl settings manager...

---

### Post by FNDII on 2007-07-13
I have it installed and everything messing with settings and stuff.

cant view it as a cube though trying hard and think of anyhting

---

### Post by FNDII on 2007-07-13
Still cant get a cube and not the change panels by moveing the mouse to the side of the screen wont work.

---

### Post by Songwind on 2007-07-13
Did you try middle-click on the background and drag?

---

### Post by FNDII on 2007-07-13
Yea i did does not seem to work.

---

### Post by Supremacy on 2007-07-13
> **FNDII said:**
> Yea i did does not seem to work.

Hold **Ctrl+Alt** and use left-click and drag to show the cube and move it.

Regards,
Supremacy

---

### Post by FNDII on 2007-07-13
I cant even click  on a window and drag it into the next desktop.

---

### Post by FNDII on 2007-07-13
Could it me my mouse?

All other options for berly are the and work, just no cube.
I have had Ubuntu for like 4 days, it has to be something real simple like a check box in options or something. I can feel it!!

---

### Post by CautionaryX on 2007-07-13
Hey, 

What video card are you using? If you're using an Nvidia card, make sure that 
```
Option      "AddARGBGLXVisuals" "True"
```

is in the Device section of /etc/X11/xorg.conf.

Also right click on the red ruby in the panel and make sure that Beryl is the window manager.

Hope this helps.

-- CautionaryX

---

