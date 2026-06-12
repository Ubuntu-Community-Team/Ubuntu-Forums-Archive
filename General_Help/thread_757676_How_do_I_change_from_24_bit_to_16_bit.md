---
title: "How do I change from 24 bit to 16 bit"
date: 2008-04-17
forum: General Help
---

### Post by roblinux on 2008-04-17
My i810 card will work with simple 3D applications if I change the default depth to 16 from 24.

I've tried gedit but can't seem to find the xorg.conf file ...

Thanks 

Rob C.

---

### Post by overdrank on 2008-04-17
> **roblinux said:**
> My i810 card will work with simple 3D applications if I change the default depth to 16 from 24.

I've tried gedit but can't seem to find the xorg.conf file ...

Thanks 

Rob C.

Hi and you can use this command ```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by roblinux on 2008-04-17
Thank you Overdrank  (done that myself frequently).

That did the trick...I can now "waste" time with pinball and ppracer etc...

Where does one find a list of this type of command for Ubuntu 7.10  ??

Rob C.

---

### Post by dsnyders on 2008-04-17
I seem to remember that  that you could switch video modes using <ctrl><alt>+ and <ctrl><alt>-  If that is still the case, you can set up your mode line with the appropriate depth/resolutions and be a keystroke away from your desired color depth.  (That's the + and - on the number pad, not on the main part of the keyboard.)

---

### Post by overdrank on 2008-04-17
> **roblinux said:**
> Thank you Overdrank  (done that myself frequently).

That did the trick...I can now "waste" time with pinball and ppracer etc...

Where does one find a list of this type of command for Ubuntu 7.10  ??

Rob C.

Hi and maybe this can help
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

---

### Post by wolfen69 on 2008-04-17
this is also good [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by roblinux on 2008-04-18
> **overdrank said:**
> Hi and maybe this can help
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/community/CommandlineHowto](https://help.ubuntu.com/community/CommandlineHowto)

Thanks again.....time to start learning !!

Rob

---

### Post by roblinux on 2008-04-18
> **wolfen69 said:**
> this is also good [http://linuxcommand.org/](http://linuxcommand.org/)


Cool...

Rob

---

### Post by roblinux on 2008-04-18
> **dsnyders said:**
> I seem to remember that  that you could switch video modes using <ctrl><alt>+ and <ctrl><alt>-  If that is still the case, you can set up your mode line with the appropriate depth/resolutions and be a keystroke away from your desired color depth.  (That's the + and - on the number pad, not on the main part of the keyboard.)

Neat shortcut....screen resolution changes instantly...

Rob C.

---

### Post by roblinux on 2008-06-14
> **overdrank said:**
> Hi and you can use this command ```
gksudo gedit /etc/X11/xorg.conf
```

Okay...Now I've upgraded to 8.04 and the xorg.conf file does not seem to have a default color depth line to edit !!??

Back to no 3D games again :(

---

### Post by roblinux on 2008-06-15
Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1440×900@60" "1600×1024@60" "1440×900@75" "1680×1050@60" "1280×800@60" "1680×1050@75" "1280×720@50" "1920×1200@60" "1280×768@75" "1280×800@75" "1280×720@60" "1280×768@60" "1280×800@60" "1280×854" "1152×720@60" "1152×768@54" "1024×768@60" "800×600@60" "800×600@75" "800×600@72" "800×600@56"
EndSubSection
EndSection


I copied and pasted the above to my xorg.conf file and changed the default depth to 16...also the depth to 16. I found it on the internet somewhere.

It now works perfect again...HOWEVER...I don't recommend anyone try this unless they are prepared to re-install the entire OS.

Rob

---

