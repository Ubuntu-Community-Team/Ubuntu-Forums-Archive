---
title: "Screen Resolution"
date: 2007-10-11
forum: General Help
---

### Post by Abhishek.Regmi on 2007-10-11
My screen resolution is stuck at 800x600. I tried some of the methods posted, and none of them had any real results. Any help would be appreciated. My current video card is NV5 [Aladdin TNT2]

---

### Post by overlord.gaurav on 2007-10-11
The screen resolutions that Ubuntu gives are the values given by you when you are installing ubuntu. These values are saved in /etc/X11/xorg.conf
Try adding the resolutions that you want to this file.

```
sudo gedit /etc/X11/xorg.conf
```

Under section: Section "Screen"  >>     SubSection     "Display" >>  Modes >> Add the resolution to all the Sub sections.
Restart X.

Here's an example of the same:    *the one highlightened is the added one*

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc M22 [Mobility Radeon X300]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768"
                [COLOR="Red"]Modes           "1280x1024"[/COLOR]
        EndSubSection

```

---

### Post by Abhishek.Regmi on 2007-10-11
After the reboot, I get an error that says that my monitor isn't registered. It gave a list of monitors that I could set it to, so I set it to my current monitor, the Test worked successfully, but after I logged in, it was still at 800x600 resolution

---

### Post by Abhishek.Regmi on 2007-10-11
The resolution's fine now, but I can't use desktop effects, and when I checked if I could run 3D items (Games -> Chess, 3D Mode) It wouldn't allow it to run. It says that my driver is installed and running, what action should I take?

---

### Post by dcstar on 2007-10-11
> **Abhishek.Regmi said:**
> The resolution's fine now, but I can't use desktop effects, and when I checked if I could run 3D items (Games -> Chess, 3D Mode) It wouldn't allow it to run. It says that my driver is installed and running, what action should I take?

What driver is selected in your xorg.conf?

You can check GLX support with the following terminal command:
```
glxinfo
```

Old Nvidia cards require the** nvidia-legacy** package, and sometime the "GLXwithComposite" option has to be set.

---

