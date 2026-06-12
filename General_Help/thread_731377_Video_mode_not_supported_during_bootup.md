---
title: "Video mode not supported during bootup"
date: 2008-03-21
forum: General Help
---

### Post by bastiac on 2008-03-21
Hello,

I have recently installed Ubuntu 7.1 but my monitor is unable to display whatever it's trying to display during bootup. However, the logon screen then displays OK. 

My config is:
Samsung SyncMaster 172w
nVidia GeForce 5900XT
driver: nVidia (installed using Envy)

Xorg.conf
Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync    30-61
        VertRefresh  56-75

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV35 [GeForce FX 5900XT]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Modes   "1280x768"      "1024x768"      "800x600"
        EndSubSection
        Option          "AddARGBGLXVisuals"     "True"
EndSection

As far as I know, all the resolutions listed are acceptable for my monitor. Anyone knows whether the bootup resolution is controlled by something else?

Cheers,
Christophe

---

### Post by rogblake on 2008-03-21
I had the same problem on an old Compaq EVO laptop running Xubuntu 7.10.

I just added the "nospash" bootup option to the kernel in /boot/grub/menu.lst, and startup messages are displayed in text mode.

---

### Post by unutbu on 2008-03-21
Please understand I am just a novice so take what I say with a healthy dose a skepticism. All the same, I hope this is accurate and helpful:

The splash screen is displayed by using the framebuffer. It has nothing to do with X. 
The login screen is drawn by gdm, which runs under X. That is why you can see the login screen but not the splash screen.

rogblake's advice should work in the sense that you avoid using the framebuffer, but perhaps you want the framebuffer to work. I think movie players like mplayer take advantage of the framebuffer -- maybe drawing directly on the screen is faster than drawing through X. (?) So to get better movie playing, you'll want a working framebuffer.

This page might help you:

[https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer)

Maybe changing your framebuffer resolution (explained in the above page) will make it work.

---

