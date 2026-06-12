---
title: "HELLP screen resolution will not go higer than 640x480"
date: 2008-06-25
forum: General Help
---

### Post by thking on 2008-06-25
my screen was working fine last night . when i booted it up this morning the screen resolution was messed up now nearly every thing is zoomed. i went to "screen resolutions" and it had no option higher than  640x480

---

### Post by cmnorton on 2008-06-25
Please look in /etc/X11/xorg.conf.

You should be able to edit this read-only to check your settings.

What's in Section "Screen" SubSection "Display"?

Here's mine:

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation G80 [Quadro FX 570M]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1920x1440" "1920x1200" "1600x1200" "1280x1024" "1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

If you cannot modify settings this through your Display configuration, then you may have to edit this file -- sudo vi /etc/X11/xorg.conf and restart X. 

Another way to do this is to reboot into recovery, and run 

dpkg-reconfigure xserver-xorg

Answer all questions taking their defaults, and only modify the section to handle the display modes you want.

Then, you can change things around in your Display Configuration.

---

### Post by jimv on 2008-06-25
What version of Ubuntu are you running?  7.10?  8.04?

What kind of video card do you have?

---

