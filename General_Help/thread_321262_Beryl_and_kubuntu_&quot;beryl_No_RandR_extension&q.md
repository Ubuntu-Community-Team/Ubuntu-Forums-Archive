---
title: "Beryl and kubuntu &quot;beryl: No RandR extension&quot;"
date: 2006-12-18
forum: General Help
---

### Post by citrusfizz on 2006-12-18
i had beryl working in kubuntu before.. but my hard drive crashed and i reinstalled....

i followed the guide to instal beryl again  and i am getting a weird error
```

XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No RandR extension

```

beryl starts  but it doesn't start the beryl windows manager

also when i load up the beryl settings  it doesn't dipslay the icons for the options and it gives this 
error
```
(beryl-settings:4748): Gtk-WARNING **: Error loading icon from file '/usr/share/pixmaps/beryl-settings.svg':
        Couldn't recognize the image file format for file '/usr/share/pixmaps/beryl-settings.svg'

```

can someone please help

i have uninstalled and reinstalled beryl like 3 times now and tried different stuff in my xorg file with no luck

i don't seem to find anything on google about the former error (unless i read french, which i cant)

thank you

---

### Post by citrusfizz on 2006-12-19
help please?

---

### Post by chadk on 2006-12-19
Do you have these installed:
libxrandr2
libxrandr-dev
xrandr

My understanding is that xrandr is only needed if you have an LCD that rotates, and you plan on rotating it.

What happens if you add this to your xorg.conf in the Section "Device" area:
```

Option          "RandRRotation" "on"

```

---

### Post by chadk on 2006-12-19
You might also try removing beryl then installing it using automatix2bleeding from [http://www.getautomatix.com](http://www.getautomatix.com)

Looks like beryl-settings.svg might be an older version (beryl-settings) than your beryl install.  What version of beryl are you using?

---

### Post by citrusfizz on 2006-12-19
I tried all the things you said and i still get the same errors

---

### Post by citrusfizz on 2006-12-19
is there a certain way i should uninstall it or files it leaves behind that i should remove..  or anything at all please?

---

### Post by citrusfizz on 2006-12-21
?

---

### Post by freerick on 2007-03-07
I have the exact same problem, beryl says the Xlib xrandr extension is missing.
Can anyone shed some light on this, I haven't found any information regarding activating the extension for the X server?

Thanks!

---

