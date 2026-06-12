---
title: "Where is the settings of X.Org?"
date: 2014-08-30
forum: General Help
---

### Post by renanrischiotto1 on 2014-08-30
Hi!

Where is the settings of X.Org now in Ubuntu? From what I've been researching the X.Org configuration file **xorg.conf** that it was kept in **/etc/X11/xorg.conf**, but then changed and now there are several files that are inside a folder called **xorg.conf.d**, but on Ubuntu there is no such folder. Where is the settings of X.Org?

Hugs!

---

### Post by Bashing-om on 2014-08-30
renanrischiotto1; Hello,

The use of "/etc/X11/xorg.conf" is depreciated and is no longer used by default. The kernel in most cases takes care of those details.
If it is required, one may make up and use one, or if a proprietary driver needs the file the driver install may make up one.
> 
 Where is the settings of X.Org?
 I say again " The kernel takes care of these details" now.

With that above, what, if any, fault are you experiencing ?

[INDENT][INDENT]what is now
[INDENT][INDENT][INDENT]may not be tomorrow
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by renanrischiotto1 on 2014-08-30
Hello Bashing-om!

See: [http://ubuntuforums.org/showthread.php?t=2241692](http://ubuntuforums.org/showthread.php?t=2241692)

I think if I could manually configure X.Org, maybe I could make it work the refresh rate of my monitor at 75Hz with the NVIDIA driver.

---

### Post by Bashing-om on 2014-08-30
renanrischiotto1;

Meeting you in that original thread.
No further action in this thread.


[INDENT][INDENT]when there is nothing to say
[/INDENT][/INDENT]

---

### Post by Frogs Hair on 2014-08-30
You might want to search create xorg conf ubuntu, but editing the file properly  once created will take some research. As stated the file hasn't been created by default for a number of releases and much of the information I found was out dated . If the Nvidia x.0rg server settings won't allow the refresh rate I would leave well enough alone unless you find a well tested method to configure the file when created.

---

### Post by deadflowr on 2014-08-30
> **renanrischiotto1 said:**
> Hello Bashing-om!

See: [http://ubuntuforums.org/showthread.php?t=2241692](http://ubuntuforums.org/showthread.php?t=2241692)

I think if I could manually configure X.Org, maybe I could make it work the refresh rate of my monitor at 75Hz with the NVIDIA driver.

If you are using the nvidia driver, and not the open-source nouveau driver, then odds are you have the nvidia packages nvidia-xserver-settings installed.
If so, then you generate an xorg.conf file using that by opening up the program, setting the values you want in the section, usually called something like "X display configuration" and then toward the bottom should be a button for save to X configuration, or something just like that.
This will create or overwrite an xorg.conf file.

If after you've done that you want make more changes, then the file will be there for you...

Added: I should probably add that if you are going to try to make manual changes to the file after the initial generation of it (when the settings should still be functional) I would suggest make a quick backup copy so if things do go south you can easily replace the bad with something good.

---

### Post by renanrischiotto1 on 2014-09-01
> [COLOR=#000000]You might want to search create xorg conf ubuntu, but editing the file properly once created will take some research. As stated the file hasn't been created by default for a number of releases and much of the information I found was out dated . If the Nvidia x.0rg server settings won't allow the refresh rate I would leave well enough alone unless you find a well tested method to configure the file when created.[/COLOR]

Interesting, thank you!

---

### Post by renanrischiotto1 on 2014-09-01
> [COLOR=#000000]If you are using the nvidia driver, and not the open-source nouveau driver, then odds are you have the nvidia packages nvidia-xserver-settings installed.[/COLOR]
[COLOR=#000000]If so, then you generate an xorg.conf file using that by opening up the program, setting the values you want in the section, usually called something like "X display configuration" and then toward the bottom should be a button for save to X configuration, or something just like that.[/COLOR]
[COLOR=#000000]This will create or overwrite an xorg.conf file.[/COLOR]

[COLOR=#000000]If after you've done that you want make more changes, then the file will be there for you...[/COLOR]

[COLOR=#000000]Added: I should probably add that if you are going to try to make manual changes to the file after the initial generation of it (when the settings should still be functional) I would suggest make a quick backup copy so if things do go south you can easily replace the bad with something good.[/COLOR]

Good idea, I'll look into it!

Well, here is the file **xorg.conf** genereted by "NVIDIA X Server Settings":

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 343.13  (buildd@lgw01-30)  Mon Aug 11 19:50:14 UTC 2014




Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection


Section "Files"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection


Section "InputDevice"


    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "Monitor"


    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection


Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400GS"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Where do I modify to change the refresh rate to 75Hz?

---

### Post by renanrischiotto1 on 2014-09-04
Solved!

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/254081](https://answers.launchpad.net/ubuntu/+source/xorg/+question/254081)

---

### Post by Bashing-om on 2014-09-04
Great !

Appreciate you providing the solution .

There are those times it takes some one 
who does know.


Happy trails to you

---

