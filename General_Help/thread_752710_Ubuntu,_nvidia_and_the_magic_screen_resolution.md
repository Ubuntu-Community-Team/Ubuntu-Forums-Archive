---
title: "Ubuntu, nvidia and the magic screen resolution"
date: 2008-04-11
forum: General Help
---

### Post by berlinbrown on 2008-04-11
They should have Mensa/GRE/College entrance exams and have a question, "How do you set your screen resolution on Ubuntu"

Anyway, I am having trouble setting my screen resolution and I had it working fine, now I going nuts trying to increase it.

Dual Monitor My setup:
OS: Ubuntu 7.10
Cards: Nvidia 5300 and 5200.
Monitors: Acer 20inches max res at 1680x1050.

What I had orginally (this worked fine for several months)
Resolution in xorg.conf: 1280x800.

This resolution worked fine but then I decided to increase my resolution to the preferred LCD settings, closer to 1680x1050.

I open nvidia-settings.

sudo nvidia-settings.

It has the resolutions:

1600x1024.  I click on both of those monitors and set the resolutions.  Everything works fine.  I say overwrite my xorg.conf.  So far, everything looks good.

But, when I logout or reboot, it doesn't keep the setting?  It sets one monitor to 1280x800 and the other to 1600x1024?  Where would it keep that setting?

A bug?

-----

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce PCX 5300"
    BusID          "PCI:2:0:0"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:5:9:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1600x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1600x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection

---

### Post by berlinbrown on 2008-04-11
I just noticed something.  When I logout, my "session" screen resolution is set to it looks like 1280x800.  E.g. the "login" prompt window.

I wonder if somehow that screen resolution is throwing off the screen resolution I want when I login.

What a mess.

---

### Post by berlinbrown on 2008-04-11
ok, I figured out my screen resolution issues.  Apparently there are 15,000 ways to configure the resolution: 1. nvidia-settings.  2. xorg.conf. 3. gnome resolution screen settings 4.  the graphics and screen settings?  wtf?

---

### Post by berlinbrown on 2008-04-11
Do the ubuntu/gnome people test their software?

Ok here is the solution.  Basically, you have to make sure that all of your "screen resolution" settings are all the same.

1. xorg.conf has dual monitors both set at 1600x1024.
2. nvidia-settings have both monitors set at 1600x1024
3. I made sure that the gnome screen resolution settings are both at 1600x0124. (System -> Preferences -> Screen Resolution)
4. I have know idea what this one does, but I made sure it was the same also: System -> Administration -> Screen and Graphics

And I still don't know why the gnome resolution setting has 50hz as the refresh rate?

---

### Post by jsundqui on 2008-04-12
I have same problem, and none of these solutions work.   I have a mythbuntu distribution, but with KDE added on.  gdm goes to my preferred resolution (1920x1200) OK, but booting into either the default mythbuntu desktop or the KDE desktop goes to 1024x768, te resolution I had before I got te big panel.

This advice:

[http://ubuntuforums.org/showpost.php?p=248755](http://ubuntuforums.org/showpost.php?p=248755)

didn't work either. 

Note, I don't have the system tools menu, but I can run the tools from the command line, and also hand edit the files under ~/.gconf

More details posted over at [http://www.gossamer-threads.com/lists/mythtv/users/329094](http://www.gossamer-threads.com/lists/mythtv/users/329094)

---

