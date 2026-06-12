---
title: "so, i think i'm missing something (beryl)"
date: 2006-11-02
forum: General Help
---

### Post by fuscia on 2006-11-02
i installed beryl using the instructions on this page - [http://www.getautomatix.com/forum/index.php?showtopic=234&hl=beryl](http://www.getautomatix.com/forum/index.php?showtopic=234&hl=beryl)

emerald and the beryl manager appear in my gnome system menu. however, it seems i can't get beryl started. am i missing something? like this xglqfbmwhatever thing?

---

### Post by 23meg on 2006-11-02
What error(s) are you getting? What's your video hardware? Are you using Edgy?

---

### Post by po0f on 2006-11-02
fuscia,

Did you install the beta NVIDIA drivers?  IIRC, you need these on Edgy to get the built-in AIGLX support for Beryl.

[EDIT]

I have it working on my box, so I'm thinking you don't have the beta driver installed.

---

### Post by fuscia on 2006-11-02
> **23meg said:**
> What error(s) are you getting? What's your video hardware? Are you using Edgy?

i'm not getting any error. i just don't know how to start it up. i'm using edgy on a system76 laptop. i have some nvidia crd with a driver i installed using automatix.

---

### Post by John.Michael.Kane on 2006-11-02
Just follow step two to get the beta drivers [http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

That should be all that you.

---

### Post by fuscia on 2006-11-02
> **SD-Plissken said:**
> Just follow step two to get the beta drivers [http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

That should be all that you.


ok, so i did all that. so now, i still have just plain gnome with the beryl-manager and some emerald thing in the system menu. so, how do i find the 'start beryl' button?

---

### Post by po0f on 2006-11-02
fuscia,

Right-click the beryl-manager icon in the tray and go to "select window manager", then choose beryl.

---

### Post by fuscia on 2006-11-02
> **po0f said:**
> fuscia,

Right-click the beryl-manager icon in the tray and go to "select window manager", then choose beryl.

(oh, doo-doo!) what tray?

---

### Post by po0f on 2006-11-02
fuscia,

Did you hit Alt+F2 and type in `beryl-manager` to start it?  The icon should be in the system tray.

---

### Post by JayTee on 2006-11-02
Try checking your installation steps against this How-To. This was the only How-To that worked for me with XGL and Beryl with an Nvidia GeForce 6200 LE.

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

---

### Post by fuscia on 2006-11-03
ok, i got it to start (adding beryl-manager to the startup thing was the answer). i have no titlebars, unfortunately, and gnome-terminal doesn't work (x-term does). i checked to make sure that screen thing was set at 24.

---

### Post by d3v1ant_0n3 on 2006-11-03
Make sure you have emerald and emerald-themes packages, then select the 'Emerald Theme Manager' option from the Beryl Settings icon. You should have a selection of themes to choose from- Does clicking one produce decoration? It should apply immediately.

There's a whole bunch of people who have had this- and similar- problems- have a read [ HERE](http://forum.beryl-project.org/topic-5639-solved-missing-window-decorations) and see if there's anything useful?

---

### Post by fuscia on 2006-11-03
emerald is installed. i tried *killall emerald*, followed by *emerald --replace* and got 


"*beryl: No GLXFBConfig for depth 32*"

---

### Post by po0f on 2006-11-03
fuscia,

Have you added the AddARGBGLXVisuals option in you Screen section?
```
Section "Screen"
    (snip)
    Option "AddARGBGLXVisuals" "true"
    (snip)
EndSection
```

---

### Post by fuscia on 2006-11-03
> **po0f said:**
> fuscia,

Have you added the AddARGBGLXVisuals option in you Screen section?
```
Section "Screen"
    (snip)
    Option "AddARGBGLXVisuals" "true"
    (snip)
EndSection
```

just did it. nothing.

---

