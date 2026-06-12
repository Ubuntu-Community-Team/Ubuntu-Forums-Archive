---
title: "dual screen how to force 3D game on left screen"
date: 2008-06-26
forum: General Help
---

### Post by dronepower on 2008-06-26
I am using a dual screen setup with a nvidia 7600GT card.

When I start a game it shows itselfs partly on the left screen, and partly on the right screen.


How can I force the game on the left screen only?

---

### Post by rubicon on 2008-06-26
Can't tell for sure, but I think Window Rules module in Compiz may help.

---

### Post by earthmeLon on 2008-06-26
What game is it?

---

### Post by 16777216 on 2008-06-26
Use ```
sudo nvidia-settings
``` to create a new meta-mode that has only one active screen and save it to your X config file ( Choose the merge option when it asks how to save. )

---

### Post by dronepower on 2008-06-28
can you explain how to do this? If I have one meta mode only one screen works.

---

### Post by 16777216 on 2008-06-28
Meta-mode is what nvidia's drivers call a set up for twinview.

For example say you have 1280x1024 @ 85Hz on the left hand monitor and the one on the right set to 1024x768 @ 75Hz, the nvidia driver would put a line like ```
Option   "metamodes" "CRT-0: 1280x1024_85 +0+0, CRT-1: 1024x768_75 +1024+0;"
``` in your xorg.conf file.

This is a meta-mode, a single combined resolution and orientation setting for both screens.

Now, running nvidia-settings normally you will not be able to save your changes to the xorg.conf file, that requires administrator privileges, this is where sudo comes in.

I am assuming you are using the 173 version of nVidia's driver.

Open a terminal ( **Applications > Accessories > Terminal** ) and type ```
sudo nvidia-settings
``` type your log-in password at the prompt and hit enter this will open the nVidia driver settings tool with administrator privileges.

On the left hand side of this window you will see a list of categories the second being **X Server Display Configuration**, click on that.

On the right of the window you will see a box ( or two or three... ) showing your current screen layout. You can click each to select it and change it's settings such as resolution, refresh rate, and orientation in relation to any other screens you may have.

This is where you will make your new meta-mode.

Click the screen-box you want to make the active one for games.
In the **Display** tab under that chose the resolution you normally use to play games at, such as 1024x768@85Hz for example.
Now click the other screen-box(s) and set it(them) to off.
Next, click the **X Screen** tab and on that tab click the **Add** button.
Now click the **Save to X Configuration** File button.
A new window will pop up with a few options, make sure the **Merge with existing file.** option is checked so any changes that other tools have made are not removed. The text entry box should have ```
/etc/X11/xorg.conf
```already in it, this is perfect. You can also preview you new xorg.conf here as well if you wish.
Simply click the **Save** button, log out and when at the log in screen push *ctrl+alt+backspace* to reset the X server so that the configuration file is reread then log back in.

Now try your game and see if that works, if so you may add more in the same fashion but you can add more than one at a time. ( The logging out after only adding one new meta-mode is to make sure that if your graphics setup gets messed up it will be easier to fix. )

By the way you can move the screen-boxes to match your real life monitor set up, such as having your screens one over the other, or if you have a gap between your monitors like me ( they mess with each other ) you can move the boxes away from each other to simulate this gap, you will have to drag windows off the screen then across the gap before it shows up on the other screen, or if one monitor is setting a little higher than the other you can simulate this here as well.

I hope this helps.
Also, open your /etc/X11/xorg.conf and save a copy before making any changes that way you have a "good working copy" to restore from in case something goes wrong.

---

### Post by dronepower on 2008-06-28
Thanks for the reply :)

I did what you wrote but now my secondary monitor keeps being turned off after turning meta options OFF for that monitor.

---

### Post by dronepower on 2008-06-30
I solved it now. my xorg.conf looked messy after using nvidia-settings a few times so I rewrote it manually.

My final xorg.conf is:

```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "P17-2"
    HorizSync       31.0 - 82.0
    VertRefresh     50.0 - 76.0
EndSection



Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
    Option     "RenderAccel"
    Option     "HWcursor"
    Option     "CursorShadow"
    Option     "CursorShadowAlpha" "32"
    Option     "CursorShadowXOffset" "3"
    Option     "CursorShadowYOffset" "3"
    Option "AddARGBGLXVisuals" "true"

EndSection



Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option      "TwinViewXineramaInfoOrder" "DFP"
    Option "SecondMonitorVendorName" "unknown"
    Option "SecondMonitorModelName" "LG L1750SQ"
    Option "SecondMonitorHorizSync" "30-83"
    Option "SecondMonitorVertRefresh" "56-75"
    Option "TwinViewOrientation"      "Leftof"
    Option         "metamodes" "DFP: 1280x1024, CRT: 1280x1024; DFP: 1280x1024, CRT: NULL; DFP: 1024x768, CRT: NULL; DFP: 800x600, CRT: NULL; DFP: 640x480, CRT: NULL;"
EndSection

Section "Extensions"
    Option         "Composite" "on"
EndSection
```

---

### Post by jazz612 on 2008-09-06
mine is a related problem.  i botched up my dual screen setup.  now i just get duplicate display on the second monitor.  how do i restore my previous dual monitor setting with screen spanning function.  help!!! i need a quick solution

---

