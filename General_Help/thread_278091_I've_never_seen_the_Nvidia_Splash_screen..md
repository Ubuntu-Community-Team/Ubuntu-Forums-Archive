---
title: "I've never seen the Nvidia Splash screen."
date: 2006-10-15
forum: General Help
---

### Post by CaveRat on 2006-10-15
I keep seeing comments here in the forum about the Nvidia Splash screen. I have the restricted drivers and nvidia turned on in zorg, but I have yet to see a splash screen. How do I check this out?

---

### Post by Dr. Nick on 2006-10-15
It appears before the login screen does, sometimes it is fast to go by. If you look in your /etc/X11/xorg.conf file it should say driver = nvidia if the drivers work properly, if it says nv then you will not see the screen.

Their is also a option in xorg.cong to hide the screen, I forget exactly whats its called though. May look for anything that mentions "splash" and "hide"

---

### Post by CaveRat on 2006-10-15
> **Dr. Nick said:**
> It appears before the login screen does, sometimes it is fast to go by. If you look in your /etc/X11/xorg.conf file it should say driver = nvidia if the drivers work properly, if it says nv then you will not see the screen.

Their is also a option in xorg.cong to hide the screen, I forget exactly whats its called though. May look for anything that mentions "splash" and "hide"

Yah nvidia is enabled in xorg.conf. I can't hardly believe this XP2400 machine is so fast I can't catch the splash. LOL

---

### Post by Dr. Nick on 2006-10-15
I swear sometimes it deosnt show up, Sometimes I see it sometimes I dont, I am not sure why exaclty, I am not home at the moment, but I know thier is a line you can add to xorg.conf to hide it, maybe yours has that line?

---

### Post by CaveRat on 2006-10-15
Not sure. Here's what xorg.conf says:

Section "Monitor"
    Identifier     "Sceptre"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Monitor        "Sceptre"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1440x900" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by Dr. Nick on 2006-10-16
dont see anything their that would block the logo out, but since your driver line says nvidia I would think the drivers are installed and working properly, maybe it has something to do with the way xorg is started or something; Dont really know

---

### Post by Naegling23 on 2006-10-16
You might not see it.  If you have a faster machine, you would miss it.  If I blink, I miss mine.

---

