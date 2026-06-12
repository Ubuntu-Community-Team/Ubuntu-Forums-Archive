---
title: "Title bars have diapered."
date: 2007-11-19
forum: General Help
---

### Post by junner18 on 2007-11-19
The title bars have diapered from all windows in ubuntu and I can't find any option to bring them back.  Anyone know why?

Also, the terminal window appears entirely white, although all functions are still accessible.

---

### Post by por100pre1 on 2007-11-19
Press ALT+F2 and then type this:

```
metacity --replace
```

---

### Post by teryowen on 2007-11-19
another way, if that doesnt work, right click anywhere on your desktop -> change desktop background -> Font

now beside window title fond make sure its the right size perhaps.

---

### Post by junner18 on 2007-11-19
I tried both suggestions... problem is still present.
The boarder around each window that you drag to resize is also gone.

---

### Post by aldenhg on 2007-11-19
Dude, I HATE it when my title bars diaper. It's all stinky and they start crying if you don't do anything about it.

---

### Post by junner18 on 2007-11-19
> **aldenhg said:**
> Dude, I HATE it when my title bars diaper. It's all stinky and they start crying if you don't do anything about it.

Look at how funny you are, cute.
I can't move or resize anything (with the mouse).  Is there anywhere I can get some quick help that doesn't have moronic comments?

---

### Post by teryowen on 2007-11-19
What were the things that you did before your last shuit down while it was still normal?

---

### Post by teryowen on 2007-11-19
I found this might help:

> 

Hi all,
I managed to fix the same/similar problem.
I installed feisty on my vaio laptop and turned on the visual effects.
None of the borders was drawn, so I couldn't move the windows around etc.

I did a couple of things... I modified the /etc/X11/xorg.conf

Section "Device"
    Identifier "nVidia Corporation NV43 [GeForce Go 6200/6400]"
    Driver "nvidia"
    Option "AllowGLXWithComposite" "true"
    Option "RenderAccel" "true"
    Option "NoLogo" "True"
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

also is set the depth bit depth to 24 (it was 16 by default)

Section "Screen"
    Identifier "Default Screen"
    Device "nVidia Corporation NV43 [GeForce Go 6200/6400]"
    Monitor "Generic Monitor"
    DefaultDepth 24
    Option "AddARGBGLXVisuals" "True"

finally, i installed the nvidia-glx-new driver thingy
in the synaptic package manager, this action removed the default nvidia-glx module
then I restarted the computer and voila!!! borders and wiggly windows!!!

somehow the cube thingy didn't work on my machine even though i checked the option in the
enable effects dialog, so i have to start it up by myself...

i made a script with these couple of lines that start it up manually...

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

now, i have to figure out why some apps render black =((

-stelios


---

