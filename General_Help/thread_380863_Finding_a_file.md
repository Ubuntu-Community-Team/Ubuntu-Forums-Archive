---
title: "Finding a file???"
date: 2007-03-10
forum: General Help
---

### Post by helliewm on 2007-03-10
I need to find the device file of my configuration to edit it?

Where exactly is it kept in the file system?

Helen

---

### Post by bernied on 2007-03-10
> **helliewm said:**
> I need to find the device file of my configuration to edit it?
Where exactly is it kept in the file system?
Helen
It's not very clear what you are asking for here. What is it that you are trying to configure?

If you know the name of the file you can use 'Find Files' on the menu, else you can use locate in a terminal. Do you know the name of the file?

---

### Post by helliewm on 2007-03-10
I have an SIS graphics cards and have installed the driver and am now getting this message see screenshot.

Helen

---

### Post by bernied on 2007-03-10
As far as I can tell, according to [this](http://www.winischhofer.eu/linuxsisusbvga.shtml#23) site, the file you want to edit is the X configuration file, which is:
/etc/X11/xorg.conf

There is probably a Device section for this graphics device, I would guess that's where you need to enable the option (not just anywhere in the file). But I am guessing here, I've never used a SiS graphics card.

[This](http://www.winischhofer.eu/linuxsisusbvga.shtml#enablesisctrl) looks like how it should be written, though it doesn't show any context.

Hopefully someone else will know about SiS graphics adaptors. You might get more help if you change your thread's topic to something like 'How do I configure my SiS graphics card?'.

---

### Post by helliewm on 2007-03-10
Bump as Title of problem has changed.

Helen

---

### Post by ~LoKe on 2007-03-10
Bernied told you what to do, what's the problem?

```
gksudo gedit /etc/X11/xorg.conf
```
Scroll down to the "Device" section and add the line:
> Option "EnableSisCtrl" "yes"

Mine would look like this:
> Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option "EnableSisCtrl" "yes"
EndSection

---

### Post by helliewm on 2007-03-10
See screenshot I am getting this error message. The XORG file appears but its blank?

Helen

---

### Post by strabes on 2007-03-10
xorg.conf is in your taskbar in that screenshot - click it on the bottom of your screen. The window you have open on that screenshot is still the terminal window. gksudo gedit /etc/X11/xorg.conf will open up a text editor.

---

### Post by helliewm on 2007-03-10
When I do that as you suggest the xorg file is empty, there is nothing to edit?

Helen

---

### Post by ~LoKe on 2007-03-10
It's case sensitive.  The "x" in X11 is capitalized.

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by helliewm on 2007-03-10
Brilliant it work, does anyone know if I can get Compiz or Beryl working now with this graphics card? I do have 1 gig of ram.

Helen

---

### Post by strabes on 2007-03-10
try this page: [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

---

