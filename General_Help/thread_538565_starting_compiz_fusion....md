---
title: "starting compiz fusion...?"
date: 2007-08-30
forum: General Help
---

### Post by freefall235 on 2007-08-30
Hey All, 

I have just installed compiz-fusion correctly, and i get the settings manager in System > Preferences....and the cube plugin is ticket.

I have added compiz -replace to my session start section, so it should start on login...

i have also tried Alt+F2 then compiz -replace in there...the window maximises and minimizes, but when i hti CTRL+ALT+Left or right, no cubage??

is there anything else i should look for?

Cheers

---

### Post by erfahren on 2007-08-30
did you set the zoom? I think the zoom out isn't set by default so it may not appear to work.

---

### Post by PmDematagoda on 2007-08-30
Did you enable rotate cube in compiz fusion? If so did you check the bindings under the rotate cube plugin options?

---

### Post by freefall235 on 2007-08-30
> **erfahren said:**
> did you set the zoom? I think the zoom out isn't set by default so it may not appear to work.

The zoom out set to <Super>Button5 (which is scroll up...)

> **PmDematagoda said:**
> Did you enable rotate cube in compiz fusion? If so did you check the bindings under the rotate cube plugin options?

Yes, the rotating cube is enabled, but still unable to activate it...

<Ctrl><alt>Button1 or <Ctrl><alt>Left/Right do nothing, its like it wont respond the keyboard shortcuts.... i just get the alt + tab (from windows) style change desktop when i press <Ctrl><Alt>Left/Right


on another side note, the wobbly windows in enabled in compiz settings, yet, wont wobble....


is there any way to tell if it is even running??

---

### Post by PmDematagoda on 2007-08-30
Did you launch compiz with 

```
compiz --replace
```?

---

### Post by freefall235 on 2007-08-30
> **PmDematagoda said:**
> Did you launch compiz with 

```
compiz --replace
```?

Hi, 

Yes, i have set it both to run at start up...and have also tried Alt + F2 and running it from there.  no go.

---

### Post by PmDematagoda on 2007-08-30
How did you install it?

---

### Post by freefall235 on 2007-08-30
by using apt get...from a clean fresh install (both compiz and ubuntu + nvidia drivers...)

---

### Post by PmDematagoda on 2007-08-30
Could you give me the command you gave to apt-get to install compiz?

---

### Post by PmDematagoda on 2007-08-30
By the way did you follow the instructions of this website in installing compiz-fusion?

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

---

### Post by freefall235 on 2007-08-30
i followed this guide...

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

Cheers

---

### Post by PmDematagoda on 2007-08-30
Whoa that's weird, okay let me just check out my own compiz-fusion settings for a bit. I'll reply as soon as I'm done.

---

### Post by PmDematagoda on 2007-08-30
Okay can you give me the list of the plugins that are active?

---

### Post by freefall235 on 2007-08-30
Plugins Currently Active:
Enhanced Zoom Desktop
Zoom Desktop
Desktop Cube
Rotate Cube
Cube Reflection
Wobbly Windows
Fading Windows 
Cube Gears
Minimize Effect
Reflection
Window Decoration
DBUS
Regex Matching
Workarounds
Move Window
Resize Window
Place Windows
Scale

All these have the default options, i havent changed anything

---

### Post by PmDematagoda on 2007-08-30
I tried with the plugins you have but the desktop cube still worked properly. When you were installing compiz-fusion were there any errors?

---

