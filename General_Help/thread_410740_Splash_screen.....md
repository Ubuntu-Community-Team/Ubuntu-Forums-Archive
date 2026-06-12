---
title: "Splash screen...."
date: 2007-04-16
forum: General Help
---

### Post by spankymasterc on 2007-04-16
anyone know how to change the splash screen??

 i want this one istead of the ugly brown one....

i had it before but i forgot lol any help would be good thnx in advance 

::Cheers::

---

### Post by josephus on 2007-04-16
in gconf-editor go to /apps/gnome-session/options/splash_image

---

### Post by ramjet_1953 on 2007-04-16
There are two great GUI programs that you can download using Synaptic that will do this for you:

1. gnome-splashscreen-manager
This just does what the name says.

2. gnome-art
Does heaps more

Regards,
Roger :cool:

---

### Post by Vord on 2007-04-16
I've done something along the lines of what josephus mentioned. Finding the folder containing the splash image and renaming the desired splash to ubuntu-splash.png and putting it in place of the original, or something along those lines. Anyone care to clarify on what he said?

---

### Post by bashologist on 2007-04-16
I made a little bash/zenity script to change splash. It checks if zenity is installed then...
```
#!/bin/bash
if which zenity; then
    splash="$(zenity --file-selection --title "select new splash image")"
    if [ -f "$splash" ]; then
        sudo ln -fs "$splash" "/usr/share/pixmaps/splash/ubuntu-splash.png"
    fi
fi

```

---

### Post by DougieFresh4U on 2007-04-16
Ok, once synaptic has done it's thingy install gnome splash screens) it puts  a launcher in System>Preferences>Splash screen. Ok, so when I open splash screen, where do I find the splah screen file? As the splash screen window is emty, Thanks

---

### Post by josephus on 2007-04-16
> **Vord said:**
> I've done something along the lines of what josephus mentioned. Finding the folder containing the splash image and renaming the desired splash to ubuntu-splash.png and putting it in place of the original, or something along those lines. Anyone care to clarify on what he said?

I originally meant that that is the key that points to the image that you want shown as your splash screen.  You can change the key to point to any other file that you like, or as you did you can overwrite the original image with your image.

Unless it didn't work I'm not sure what you type of clarification you are looking for.

---

### Post by spankymasterc on 2007-04-17
There u go gnome-splashscreen-manager is what i had thx alot :D

---

