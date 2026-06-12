---
title: "nvidia-settings problem"
date: 2007-02-18
forum: General Help
---

### Post by notjohn101 on 2007-02-18
i have the samew problem so i did
gksudo nvidia-settings

and it opened....but

theres no...

"xserver display configuration"

and i need it to change the refresh rate of my monitor, its locked at 85Hz....it needs to go down to 60Hz

---

### Post by yabbadabbadont on 2007-02-18
nvidia-settings is run as your normal user.  No need for sudo or gksudo.  When I ran it though, it didn't have any options for changing the refresh rate...  Perhaps you are thinking of a different utility?  (nvidia-xconfig maybe?)  Normally, I just edit my /etc/X11/xorg.conf file directly (you would have to use sudo) and make the necessary changed there.
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-69
        VertRefresh     50-80
        DisplaySize     306 230
        Gamma           0.75 0.75 0.75
EndSection

```
The HorizSync is the horizontal sync rate in kHz and the VertRefresh is the vertical refresh rate in Hz.

---

