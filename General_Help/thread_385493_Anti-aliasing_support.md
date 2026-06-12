---
title: "Anti-aliasing support?"
date: 2007-03-15
forum: General Help
---

### Post by solinent on 2007-03-15
Hi there :) 

I'm fairly new to ubuntu.  I first tried out general usage and things like that, and I feel I'm good at doing stuff through there now.  So I'm in-experienced, but not stupid, hopefully.

So here's my problem.  I want to enable anti-aliasing support for beryl, through nvidia-settings.  However, this is the message I get:

```

adrian@solinent-desktop:~$ nvidia-settings

ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.

```

Now, the GUI does launch, but it is very minimal, with options for:
[list]
[*]Enable Tooltips
[*]Display status bar
[*]Slider text entries
[*]Include X display names in config file
[*]Show "Really Quit?" dialog
[/list]
After those checkboxes, I can either "quit" or go to "help" which explains everything nicely.

So, can some one help me?

Asus nVidia 6600GT
AMD64 athlon 4400+ X2 (I am not running AMD64 ubuntu)

---

### Post by SishGupta on 2007-03-15
Is your 3d working? you said you are using beryl so id assume yes but lets check anyway.

check by going to the terminal and typing:
```

glxgears

```
if you see 3d gears, your 3d is working.

if it isnt working You don't have the nvidia driver installed and you are using the open source driver that comes with ubuntu.

Try
```

sudo apt-get install nvidia-glx

```

restart and once again try
glxgears

got 3d? nvidia-settings should work now.

---

### Post by solinent on 2007-03-15
Sorry for late response, was trying to get another package (eclipse-cdt) to work.

Anyways, thanks, but glxgears does run. (beryl works fine also).

The only problem is that I want to see more options under nvidia-settings so I can enable anti-aliasing.

Thanks :)

EDIT: I see now that I need to enable the "Coolbits" option -- however this is not working (I edited xorg.conf).

Here's the coolbits part in xorg.conf:
```

Section "Device"
    Identifier     "NVIDIA GeForce 6600 GT"
    Option         "Coolbits" "1"  ### enables complete nvidia-settings
    Driver         "nvidia"
EndSection

```

I have restarted (ctrl alt backspace) but it doesn't work.  I have also tried restarting the entire computer after modifying xorg.  I think that error I got has something to do with it.

---

### Post by solinent on 2007-03-15
Is this what I need?  I downloaded it and it says I need to exit X server.  How do I do that (I've only done it when it crashes :lolflag: 

[http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

---

### Post by solinent on 2007-03-17
I've gotten nvidia-settings to work, but the settings seem to have no effect.
```

beryl-settings -c :0

```

What do I have to do?

---

