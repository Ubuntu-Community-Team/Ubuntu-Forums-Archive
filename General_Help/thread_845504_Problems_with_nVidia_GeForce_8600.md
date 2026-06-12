---
title: "Problems with nVidia GeForce 8600"
date: 2008-06-30
forum: General Help
---

### Post by janki on 2008-06-30
I have installed Ubuntu 8.04 on my Fujitsu-Siemens laptop. To utilize the graphics card I decided to enable it via *System* > *Administration* > *Hardware Drivers*. The graphics card I have in the laptop I found using the command *lspci*:
----
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
----

My display has a maximum resolution of 1440x900 pixels, but now the maximum resolution I can choose under *System* > *Preferences* > *Screen Resolution* is 1024x768 pixels. Before I enabled the NVIDIA accelerated graphics driver the display was set to the maximum resolution. How can I once again make Ubuntu detect the maximum resolution of the display, and set the screen resolution to this value?

I appreciate any help I can get on this matter. Thanks!

---

### Post by Mikecore on 2008-06-30
> **janki said:**
> I have installed Ubuntu 8.04 on my Fujitsu-Siemens laptop. To utilize the graphics card I decided to enable it via *System* > *Administration* > *Hardware Drivers*. The graphics card I have in the laptop I found using the command *lspci*:
----
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
----

My display has a maximum resolution of 1440x900 pixels, but now the maximum resolution I can choose under *System* > *Preferences* > *Screen Resolution* is 1024x768 pixels. Before I enabled the NVIDIA accelerated graphics driver the display was set to the maximum resolution. How can I once again make Ubuntu detect the maximum resolution of the display, and set the screen resolution to this value?

I appreciate any help I can get on this matter. Thanks!

you could install a program called "nivida x server settings" or open the 
"System Preferences and then screen resolution" Both have a "detect monitor" function that might help you or finally if all else fails you can look up your monitor specs and manually add a mod line to your x server config ( in /etc/X11/xorg.conf )

---

### Post by janki on 2008-07-03
Thanks for your reply!

Perhaps my display is too new to be detected by Ubuntu? It just says *Unknown* for display type.

I looked through the *xorg.conf*-file. Under the section *Screen* I have the following:
====
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
====
How do I modify this so that the screen resolution is set to 1440x900 pixels? Do I just add "1440x900" to *Modes*?

---

### Post by pedro_orange on 2008-07-03
You can try specifying what resolutions your monitor can display.
You can either edit your xorg conf file or you can do a:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

One of the steps in there asks you to choose resolutions that your monitor can display. So go for it.

---

### Post by jimv on 2008-07-03
> **pedro_orange said:**
> You can try specifying what resolutions your monitor can display.
You can either edit your xorg conf file or you can do a:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

One of the steps in there asks you to choose resolutions that your monitor can display. So go for it.

In 8.04, reconfiguring the xserver no longer lets you choose your resolution.  Yes, sad.

I would try using EnvyNg to isntall the latest Nvidia driver and see if that helps.

---

### Post by pedro_orange on 2008-07-04
> **jimv said:**
> In 8.04, reconfiguring the xserver no longer lets you choose your resolution.  Yes, sad.

I would try using EnvyNg to isntall the latest Nvidia driver and see if that helps.

No way!

Thanks for the heads up!

---

### Post by janki on 2008-07-05
I installed *EnvyNg*, and it correctly detects my grapchics card. It also says that my grahics card is supported by the driver. However, when I try to change the resolution in *System* > *Preferences* > *Screen Resolution* (after the recommended restart) the maximum is still only 1024x768 pixels. And it still says that my display is unknown. Isn't there somewhere in the settings where I can just enter the resolution of my display?

---

