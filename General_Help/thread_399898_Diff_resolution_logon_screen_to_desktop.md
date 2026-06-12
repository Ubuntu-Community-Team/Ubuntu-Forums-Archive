---
title: "Diff resolution logon screen to desktop"
date: 2007-04-02
forum: General Help
---

### Post by Clay_Banger on 2007-04-02
when i first boot my computer up, it has a really large resolution for the logon screen, im thinking 1600 x 1200, when i logon it changes down to the resolution i have set 1280 x 1024 which is the largest my monitor is supposed 2 handle. and if i try to change the resolution to 1600 x 1200 i get the "input out of range signal". how do i change the resolution that the logon screen uses? or can i find out what it is using and use that as my resolution when im logged in?

---

### Post by kellemes on 2007-04-03
Edit your xorg.conf and insert the specific resolution you want to use..

This is the section of my xorg.conf where the resolution should be.

```
Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1680x1050"
        EndSubSection
EndSection

```

---

### Post by Clay_Banger on 2007-04-03
my xorg.conf has this:

```
Section "Screen"
  Identifier "Default Screen"
  Device "Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1280x1024@60" "1280x960@75" "1280x960@85" "1400x1050@60" "1280x960@60" "1400x1050@75" "1280x1024@75" "1600x1200@65" "1280x854" "1600x1200@60" "1152x768@54" "1600x1200@70" "1152x864@75" "1792x1344@60" "1024x768@43" "1856x1392@60" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection
```

how do u i tell which one of these possible values it is using without using trial and error?

---

### Post by kellemes on 2007-04-04
I don't the refreshrate for your monitor so you have to find out yourself..
Probably there will be info on this in your /var/log/Xorg.0.log

So, get the one resolution you need and delete the rest..

---

### Post by kvarley on 2007-04-06
I have a HP Pavilion f1523 monitor and I can view the installation of Ubuntu but then the monitor pop's up a message. "Input out of range" Anybody know how to fix this?

---

