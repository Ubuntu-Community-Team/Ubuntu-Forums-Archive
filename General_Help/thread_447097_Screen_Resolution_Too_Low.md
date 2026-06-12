---
title: "Screen Resolution Too Low"
date: 2007-05-17
forum: General Help
---

### Post by mpgarate on 2007-05-17
When I boot from the Ubuntu CD (7.04) I cannot change the screen resolution to be bigger than 1024 by 768. My monitor is capable of 1800 by 1024 (or something like that) and everything looks bloated when compared to windows. How can I change the resolution bigger?

---

### Post by spamking2000 on 2007-05-17
Once booted up, have you gone to System -> Preferences -> Screen Resolution and tried to change it there? Sounds like you have a widescreen monitor... one guess is that maybe you have an unusual video card to go with it? If that's the case, there might not be native support for the video card and 1024x768 may be all that you can get without a 3rd party driver... which of course wouldn't be on the Ubuntu Live CD.

---

### Post by Death_Sargent on 2007-05-17
what kind of video card are you using

for intel cards be sure to install 915resolution

---

### Post by mpgarate on 2007-05-17
dell nvidea integrated graphics, brand new PC, not widescreen, I should have said 1280 by 1024.. and the max is 1024 by 768 (under system>preferences>screen resolution)

I tried installing that package, but it detected that I wasnt using that card

---

### Post by LostBear on 2007-05-17
i have this exact same problem with a clean install of xubuntu (feisty. i have a radeon 9250se and cant go higher. this wasnt a problem with ubuntu feisty or previous versions. 

i havent touched the drivers although i have installed beryl. cant put screen above 1024 x 768 in the display preferences. 

any thoughts?

---

### Post by mpgarate on 2007-05-17
I tried following a few tutorials (from googling "Ubuntu screen resolution") that messed up my X. Had to re install a few times.

---

### Post by mpgarate on 2007-05-17
[COLOR="Red"]_EDIT: THE FOLLOWING DOES **NOT** WORK_[/COLOR]

Here is what Im Trying Now:

> gksudo gedit /etc/X11/xorg.conf

Where it says "Section "Screen""
Scrol Down To "SubSection     "Display""
and add: "1280x1024" to the beggining of each

heres what my whole Screen Section Looks Like:
> Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation C51 [GeForce 6150 LE]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


I will edit this post with the results

edit: did not work. after a restart, system>preferences>screen resolution> gave the same 3 resolutions. I then restored my xorg.conf

---

### Post by mpgarate on 2007-05-17
FIXED! Followed [these instructions]("http://ubuntuforums.org/showthread.php?t=447023&highlight=screen+resolution"):

> yes there is a way to fix your resolution: run the command
Code:

sudo dpkg-reconfigure xserver-xorg

from a terminal, and answer all the questions. When you get to the part about what screen resolutions you have, scroll and select 1280*1024. 


Then I did a control+alt+backspace, then I noticed the login screen was in 1280 by 1024. I logged in, gave me the old, small resolution. went to system>preferences>screen resolution, and the larger choice was there! If you have specific questions about this, feel free to PM me!

---

