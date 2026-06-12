---
title: "[SOLVED] nvidia-settings-rc &amp;quot;No Display Connection&amp;quot;"
date: 2008-05-01
forum: General Help
---

### Post by greyfox1 on 2008-05-01
Hello,

While trying to solve my wobbly windows tearing issue described [here]("http://ubuntuforums.org/showthread.php?t=709851"), I've come across a new issue since upgrading to Hardy.  

Whenever I try to load my nvidia settings (Either by issuing "nvidia-settings -l" or "nvidia-settings --load-config-only", I get the result below.  I can bring up the nvidia-settings tool without any apparent issues.

```

rick@rick-desktop:~$ nvidia-settings -l

ERROR: Cannot open display 'rick-desktop:0.0'.


ERROR: Unable to assign attribute DigitalVibrance specified on line 21 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ImageSharpening specified on line 22 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute SyncToVBlank specified on line 23 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute AllowFlipping specified on line 24 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAniso specified on line 25 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAA specified on line 26 of configuration
       file '/home/rick/.nvidia-settings-rc' (no Display connection).


ERROR: Unable to assign attribute TextureSharpen specified on line 27 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute ForceGenericCpu specified on line 28 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GammaCorrectedAALines specified on line 29 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadow specified on line 30 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowXOffset specified on line 31 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowYOffset specified on line 32 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowAlpha specified on line 33 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowRed specified on line 34 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowGreen specified on line 35 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute CursorShadowBlue specified on line 36 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute FSAAAppControlled specified on line 37 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute LogAnisoAppControlled specified on line 38 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GPUScaling specified on line 39 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedBrightness specified on line 40 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenBrightness specified on line 41 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueBrightness specified on line 42 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedContrast specified on line 43 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenContrast specified on line 44 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueContrast specified on line 45 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute RedGamma specified on line 46 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute GreenGamma specified on line 47 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute BlueGamma specified on line 48 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute OpenGLImageSettings specified on line 49 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoTextureSyncToVBlank specified on line
       50 of configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoBlitterSyncToVBlank specified on line
       51 of configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).


ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52 of
       configuration file '/home/rick/.nvidia-settings-rc' (no Display
       connection).

rick@rick-desktop:~$

```

I'm at a loss.  Searches of these forums and Google haven't turned up any solutions.  Any help will be GREATLY appreciated.

---

### Post by greyfox1 on 2008-05-02
bump

---

### Post by greyfox1 on 2008-05-03
bump

---

### Post by greyfox1 on 2008-05-04
bump

---

### Post by RAOF on 2008-05-05
Does running nvidia-settings as your user (without using sudo, which is unnecessary) work?  Can you run nvidia-settings normally, bringing up the GUI?

---

### Post by greyfox1 on 2008-05-05
My mistake, I should have included those details.  The terminal session I pasted does show me issuing the command as root (just because I was trying whatever I could think of to try to get this to work) but I normally load the nvidia settings as a normal user, not root.  I can bring up the nvidia settings tool ("gksudo nvidia-settings") without any apparent issues.  OP edited.  Hope this helps!

---

### Post by RAOF on 2008-05-05
Right.  So you can load it as root (with gksudo), but not as your user.  This suggests a permissions problem.  Maybe.

What happens if you try "DISPLAY=:0.0 nvidia-settings"?  The rick-desktop hostname in the DISPLAY nvidia-settings is trying to use is somewhat surprising; I don't have such an element to my $DISPLAY.

---

### Post by greyfox1 on 2008-05-06
I can run nvidia-settings as a normal user-- never said I couldn't.  Isn't it true that nvidia-settings should be run as root so that the settings can be saved properly?

At any rate, whether I issue "DISPLAY=:0.0 nvidia-settings" or plain old "nvidia-settings", the NVIDIA X server Settings dialog opens normally, but I get the same output in my terminal as I referenced in the original post.  Hope this helps.

---

### Post by RAOF on 2008-05-07
Sorry, it seems I'm a bit confused.  So I'll say some things that I know to be true :).

It's not necessary to run nvidia-settings as root.  You'd only want to do this if you hardcode your TwinView configuration in xorg.conf (which seems a pretty silly idea, dynamic twinview works pretty well) and you wanted to change the configuration.  None of the other options settable by nvidia-settings are saved in xorg.conf, or anywhere not-user-local.  Which is why you need to run nvidia-settings --load-config-only in the first place :).

My guess is that .nvidia-settings-rc contains entries for the display "rick-desktop:0.0", which doesn't exist at the moment, hence the errors.  I'd try moving your .nvidia-settings-rc file somewhere out of the way, then running nvidia-settings again to create a new one.  Does that work?

---

### Post by greyfox1 on 2008-05-07
Yeah that did the trick. Thanks my man.  Each line in my old .nvidia-settings-rc did begin with "rick-desktop:0.", which does not appear in the newly created file.  I really don't know how they got there.  I didn't manually edit the file -- in fact, I don't recall ever hearing about .nvidia-settings-rc before I ran into this problem.  Strange.

Now if I could just get my [tearing issue]("http://ubuntuforums.org/showthread.php?t=709851") resolved, I'd be golden.

---

### Post by jstgtpaid on 2008-06-03
I had the same problem, but I noticed that if I unchecked 'include X display names' in the nvidia-settings Configuration that also fixed the problem...

---

### Post by Ux64 on 2008-08-12
Own thread for this (my) problem:
[http://ubuntuforums.org/showthread.php?t=887762](http://ubuntuforums.org/showthread.php?t=887762)

--

I have kind of similar issue. I have two X Screens using Xinerama config.

But I'm unable to set contrast for secondary screen. I wonder how that can be done.

I think I have tried everything, but I still fail. And usually get error like:

```

ERROR: Invalid X Screen 1 specified on line 57 of configuration file
       '.nvidia-settings-rc' (there is only 1 X Screen on this
       Display).

```

What I should specify on that line? Old line started with 0 so I added contrast configuration with prefix 1.

Here is my Nvidia-Settings configuration screen:
[http://img139.imageshack.us/my.php?image=settingsoi2.png](http://img139.imageshack.us/my.php?image=settingsoi2.png)

TV-0 is the screen #1 and I should lower contrast by something like 10%.

I tried it using row:

```
1/RedContrast=-0.100000
1/GreenContrast=-0.100000
1/BlueContrast=-0.100000

```

---

### Post by mcurran on 2009-01-25
I had the wobbly windows tearing with compiz and then had the same errors show up while trying to correct the tearing.  I fixed the errors by following your instruction, and removing the name configuration check mark in nvidia-settings.  The tearing is now gone, because I maxed-out everything in nvidia-settings and then saved the configuration to xorg.  If anyone wants to try my fix; be sure to overwrite the file by unchecking the merge option in nvidia-settings before saving to xorg.  I then used the general options under the compizconfig settings manager app. and enabled synch to vblank there, and also manually adjusted the refresh rate to match mine (60FPS).  Here's my xorg.conf below - I have an ASUS G1Sn with a NVIDIA 9500M GS, in case my example will be of use to anyone else trying to get rid of the tearing.



**[SIZE="4"]xorg.conf[/SIZE]**

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Mon Nov  3 08:46:04 UTC 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500M GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



**[SIZE="4"].nvidia-settings-rc[/SIZE]**

#
# /root/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Sun Jan 25 22:03:38 2009
#

# ConfigProperties:

RcFileLocale = C
ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes
Timer = Thermal_Monitor_(GPU_0),Yes,1000
Timer = PowerMizer_Monitor_(GPU_0),Yes,1000

# Attributes:

0/DigitalVibrance[DFP-0]=0
0/SyncToVBlank=1
0/AllowFlipping=1
0/LogAniso=4
0/FSAA=12
0/TextureSharpen=1
0/CursorShadow=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/FSAAAppControlled=0
0/LogAnisoAppControlled=0
0/GPUScaling[DFP-0]=131073
0/FSAAAppEnhanced=1
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/OpenGLImageSettings=0
0/XVideoTextureBrightness=0
0/XVideoTextureContrast=4096
0/XVideoTextureHue=0
0/XVideoTextureSaturation=4096
0/XVideoTextureSyncToVBlank=1
0/XVideoSyncToDisplay=65536



[SIZE="4"]**CompizConfig Settings Manager (General Options > Display Settings):**[/SIZE]

Texture Filter:               Best
Detect Refresh Rate:          (checked)
Lighting:                     (checked)
Refresh Rate:                 60
Synch To VBlank:              (checked)
Detect Outputs:               (checked)

---

