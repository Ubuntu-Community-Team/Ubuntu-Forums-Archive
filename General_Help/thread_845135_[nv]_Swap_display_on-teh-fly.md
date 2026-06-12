---
title: "[nv] Swap display on-teh-fly"
date: 2008-06-30
forum: General Help
---

### Post by Redsandro on 2008-06-30
I know this question came by in a lot of flavours a lot of times. I've read a lot of them. And think it's weird there are not a million how-to's, since there's a lot of how-to's about less important stuff.

Bottom line, the nvidia drivers do not support this on the fly stuff and overlay rendering for easy access. Many people suggested using different xsessions for different displays. It worked before when adding the following to my xorg.conf:

```
# TV only
Section "ServerLayout"
    Identifier     "tv"
    Screen      0  "Screen_TV" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Screen" 
    Identifier     "Screen_TV"
    Device         "Card_TV"
    Monitor        "Monitor_TV"
    DefaultDepth    24
    Option         "metamodes" "TV: 720x576 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "720x576"
    EndSubSection
EndSection

Section "Device"
    Identifier     "Card_TV"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Option         "NoLogo"
    Option         "TVOutFormat" "SVIDEO"  # Or "COMPOSITE"
    Option         "TVStandard" "PAL-B"
    Option         "ConnectedMonitor" "TV"
    Option         "TwinView" "1"
    Screen 0
EndSection

```

When editing a separate layout, you can test this by entering:
*$ **sudo startx -- :1 -layout "tv"***
If you get this extremely interesting grey screen with the best default mouse cursor ever, you now the layout works!

This way, opening a movie on the tv is no problem:
*$ **sudo xhost +;sudo xinit vlc -fs \"**[movie path+name]**\" -- :1 -layout tv***

[SIZE="1"](strangely though, this in my scripts folder, meant to make things easy, did not work. Tried a lot of things, also gksudo instead ofcourse:
```
#!/bin/bash
if [ -z $1 ]; then # No files selected
    zenity --error --title "No files selected" --text "Select some files to play on TV."; 
    exit;
else
    sudo xhost +;sudo xinit vlc $1 -- :1 -layout clonetv
fi
```)[/SIZE]

I was annoyed by needing to entering a password to access my own television and not being able to use my monitor at the same time, like my laughing housemate has no problem with in XP. Apart from that, it worked until I upgraded from *Ubuntu* **7.10** to **8.04**. Now this joke makes either my tv or monitor green-purple after switching once:


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=75789&stc=1&d=1214833000[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=75788&stc=1&d=1214833000[/IMG]

So.. decided to give some form of cloneTV a shot. Since a PAL tv can have 1024 as input, I decided to make an exact clone, ressing down my main monitor to 1024 as well. Sucks for work, but perfect for 'movie-mode':

```
# TV clone of Monitor @ 1024
Section "ServerLayout"
    Identifier     "clonetv"
    Screen      0  "Screen_Clone" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Screen"
    Identifier     "Screen_Clone"
    Device         "Card_VGA"
    Monitor        "Monitor_TFT"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: 1024x768 +0+0, TV: 1024x768 +0+0"
    Option         "TVOutFormat" "SVIDEO"  # Or "COMPOSITE"
    Option         "TVStandard" "PAL-B"
    Option         "RenderAccel" "On"
    Option         "HWcursor" "On"
    Option         "DamageEvents" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Device"
    Identifier     "Card_VGA"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:1:0:0"
    Option         "NoLogo"
    Option         "TwinView" "1"
    Screen 0
EndSection
```

Not very good, still requiring password and stuff, also makes my monitor greenpurple.

Finally I read people recommending using *nvidia-settings* to create a ~/.nvidia-settings-rc for every layout and use that by loading the config on the fly. Good idea for some cases, but the settings file seems not to store any resolution or display related info other than some color correction. It was noted in other topics that **xrandr** could steer settings. Getting only the proper settings could be learned by comparing ($ diff -u) two .nvidia-settings-rc's, but I don't get any difference. The idea would be cool.

I **do** know that, using nvidia-settings and 20 mouseclicks, I can swap to a full clone mode for video and back without colors going greenpurple and without entering a password. So it is possible. How? Can anybody point me in a direction what to try next?

---

### Post by Redsandro on 2008-07-02
Figured it out. Metamodes will help using other tools to swap. Try googling metamodes, not a page in the first million hits that will explain what it is, so maybe you can do more with trial and error that I dont know yet.

Here's a little howto. Tested only on my Nvidia.

Imagine your optimal monitor resolution being 1280x1024. No need to use anything else. You can create a twinview tv clone that spans only part of your main screen with nvidia-settings and save a xorg.conf.

Next, change your metamodes option so it has your main monitor resolution with NULL for tv and 1280x1024 for crt first, followed by both the tv and crt at 1024 (maximum tv res, easy on the eyes with the monitor):

**Option "metamodes" "CRT: 1280x1024 +0+0, TV: NULL; CRT: 1024x768 +0+0, TV: 1024x768 +0+0"**

(backup xorg,conf first)

Restart x, should get working display.

Now create two launchers in your task panel and give them cool icons.

**Name:** Display Desktop mode
**Command:** xrandr -s 0

**Name:** Display TV mode
**Command:** xrandr -s 1

Tadah! Nice swap without needing password. If you don't get it right do some trial and erroring. I don't know about a nicer way or overlay rendering. If you do, please post.

---

