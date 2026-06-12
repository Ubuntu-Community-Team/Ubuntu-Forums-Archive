---
title: "Trouble with Nvidia drivers and OpenGL"
date: 2007-12-28
forum: General Help
---

### Post by freehunt on 2007-12-28
I tried to install Glest the other day, and it told me it needed OpenGL 1.3, and all I had was OpenGL 1.2. Google Sketchup in Wine tells me I have no OpenGL, as does the OpenGL command line test (can't remember what it is right now). I have the nvidia-glx-new drivers installed, and my card is a GeForce 7800 in a Dell Inspiron E1705 from before Ubuntu was installed on Dell laptops. I have the restricted drivers enabled, and Compiz is working like a charm, including the 3D desktop. How do I get OpenGL? I've uninstalled and reinstalled these drivers a few times, but nothing works, and I don't know the command line well enough to jump through the hoops needed to install the binary drivers from nvidia.com.

---

### Post by empthollow on 2007-12-28
it sounds like you are trying to install sketchup in wine which is a windows api emulator. it says you have no open gl because wine has no open gl.  linux has open gl for native linux programs.  i'm not sure you can get open gl for wine but i'm not sure you can't either.

---

### Post by freehunt on 2007-12-28
I know that Wine has to support OpenGL, otherwise there wouldn't be 3D and all that. I've run Half Life 2 in Wine using OpenGL. That doesn't really solve my Linux-native problem, though.

---

### Post by empthollow on 2007-12-28
that's a dang good point, i've used open gl in wine before too.  can't believe i overlooked that.

---

### Post by freehunt on 2007-12-30
So, I'm still having an issue with OpenGL, I can't figure out what I need to do to make it work.

---

### Post by empthollow on 2007-12-30
i found this great info on winehq....

> after the first run i got this every time i launched sketchup

SketchUp was unable to initialize OpenGL!
Please make sure you have installed the correct
drivers for your graphics card
Error: ChoosePixelFormat failed

so i went into regedit: HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display\HW_OK

change the value to 1. starts and runs fine. still crashes on save, but when resuming the autosave was still there and reloaded my drawing.

wine 0.9.39
sketchup 6.0.515

> after the first run i got this every time i launched sketchup

SketchUp was unable to initialize OpenGL!
Please make sure you have installed the correct
drivers for your graphics card
Error: ChoosePixelFormat failed

so i went into regedit: HKEY_CURRENT_USER\Software\Google\SketchUp6\GLConfig\Display\HW_OK

change the value to 1. starts and runs fine. still crashes on save, but when resuming the autosave was still there and reloaded my drawing.

wine 0.9.39
sketchup 6.0.515

this information was found at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842\](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842\)


hope that helps you out.

---

### Post by freehunt on 2007-12-31
I tried that, still has the same effect. I'm sure it would work if I did have OpenGL working, but it seems I don't, the Cedega tests fail on OpenGL as well.

---

### Post by empthollow on 2008-01-01
what video card do you have?

---

### Post by freehunt on 2008-01-01
In my first post, I posted that I have a Geforce 7800 in a Dell Inspiron E1705 from before Dell put Ubuntu on laptops.

---

### Post by empthollow on 2008-01-01
could it possibly be an xorg.conf issue like loading a particular module like dri or glx?  i didn't have to mess with that when i got my nvidia card but each situation is different.  otherwise you could try :```
sudo dpkg-reconfigure nvidia-glx-new
```
i'm not sure what that would do, to do a re-write of xorg.conf you can do
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by freehunt on 2008-01-01
It's strange, because I never had this problem with Feisty, I would run Glest and Half Life 2 on it with no problem, even on an external monitor. It seemed back then there were more options for card drivers, and I had some kind of settings program installed that I can't recall right now.

Anyway, I tried both of those options, still no dice.

---

### Post by empthollow on 2008-01-01
hmm...
how about
```
sudo nvidia-glx-config enable
```

also, i just found a nvidia settings program you can access it by typing
```
nvidia-settings
```
there is an opengl section in that prog

---

### Post by freehunt on 2008-01-01
I ran nviidia-settings before and it would say I'm not using the nvidia driver for X, and not give me any options. I tried the first command you gave me, and it says my xorg.conf is wrong, that I should be using the nvidia driver not the nv driver, and I just checked, I AM using nvidia, not nv.

---

### Post by empthollow on 2008-01-01
i don't think compiz would work if you were using the nv driver.  is the kernel module loaded, you can check with```
lsmod | grep nvidia
``` if you like i can post my xorg.conf to compare, i have everything working with geforce 6200le on gutsy.  You can post yours if you'd like and i'll take a look at it.

---

### Post by freehunt on 2008-01-01
This is the result of the command you asked me to run
:```
nvidia               7856768  36 
i2c_core               25104  1 nvidia
agpgart                33584  2 nvidia,intel_agp

```

Here is the contents of /etc/X11/xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:09:35 PST 2007


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by empthollow on 2008-01-01
i have 2 differences in my xorg.conf
1.  in section "module"
i have a 
```
load       "v41"
```
in addition to glx and in the device section under vendor name
```
screen 0
```
i'm not sure what v41 is but i think screen 0 could be important.

---

### Post by freehunt on 2008-01-01
It seems like those could be attributed to differences in hardware?

---

### Post by empthollow on 2008-01-01
i think the v41 could be, i know that the screen 0 tells X what screen to use.  i'm not sure that would make a difference but other than removing and re-installing the drivers i can't think of anything else right now.  i'll let you know if i do though.

---

### Post by freehunt on 2008-01-02
Odd, I just restarted again, and the nvidia logo came up during boot. It allowed me to install Glest, but Sketchup still does not work. Might have to retry that workaround posted earlier. Another, smaller issue that has just surfaced, my laptop's touchpad has stopped working properly. The scrolling sections don't scroll, and double tapping and moving my finger doesn't drag anymore. Oh well, all that needs is some tinkering in the xorg.conf files again, no big deal. Hey thanks for the help though, something you guys had me do worked, it just took two restarts for it to take effect! Much love.

(gaaaah, tried to scroll down to hit submit using the scrolling area... no dice. Gotta remember that until I get a chance to fix it)

---

### Post by empthollow on 2008-01-02
see if this link helps you with the touchpad.  [http://ubuntuforums.org/archive/index.php/t-3993.html](http://ubuntuforums.org/archive/index.php/t-3993.html)

---

### Post by freehunt on 2008-01-02
Son of a gun, I fixed my touchpad by myself, I've done it before. However, after a restart... OpenGL doesn't work. The nvidia logo still comes up on boot, but Glest still says I need to have OpenGL 1.3 installed.

---

### Post by altonbr on 2008-01-17
I have Ubuntu Gutsy 7.10, nVidia 6800, nvidia-glx-new WAS installed, before I ran 'sudo dpkg-reconfigure xserver-xorg' and in both situations I also get "SketchUp was unable to initialize OpenGL!".

The odd thing is, I was the user that submit Google SketchUp as working like 'silver' in the WineHQ: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842&iTestingId=16760](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842&iTestingId=16760)

For the record...

BEFORE
Ubuntu Gutsy 7.10
2007-10-23
Wine 0.9.47. 

NOW
Ubuntu Gutsy 7.10
2008-01-17
Wine 0.9.53

I've had the same video card for both, wiped Ubuntu in between tries and am using the WineHQ version of Wine, not Ubuntu's.

This regedit fix doesn't work...
> **empthollow said:**
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842\](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6842\)


And neither do these commands...
> **empthollow said:**
> could it possibly be an xorg.conf issue like loading a particular module like dri or glx?  i didn't have to mess with that when i got my nvidia card but each situation is different.  otherwise you could try :```
sudo dpkg-reconfigure nvidia-glx-new
```
i'm not sure what that would do, to do a re-write of xorg.conf you can do
```
sudo dpkg-reconfigure xserver-xorg
```

I just ran 'sudo nvidia-glx-config enable' and it returned:
> A backup of xorg.conf has been stored as:
/var/backups/xorg.conf.2008-01-17-22:48:47.
If the new configuration will not work you will be able to
revert the changes simply using this command:
cp /var/backups/xorg/xorg.conf.2008-01-17-22:48:47 /etc/X11/xorg.conf


Warning: your X configuration has been succesfully changed.
In order to take full advantage of the changes, X needs to
be restarted.

So I will report back after my reboot.

The really odd thing was, I installed Google Sketchup, and it was loading, then I disabled Compiz ("just in case," I thought), then had to force quit Google Sketchup and now I receive this error all the time.

I then deleted ~/.wine, purged my Wine install and then ran 'sudo dpkg-reconfigure xserver-xorg' and now I'm here.

---

### Post by altonbr on 2008-01-17
Well, 'sudo nvidia-glx-config enable' completely screwed over my display, so now I don't know what else to do to fix Google Sketchup...

Anyone get it working or know of any alternatives...?

---

### Post by utterlyjaded on 2008-02-25
i am having this same problem where i cant seem to get opengl enabled, a flash seems to come up everytime i try to run something using opengl, annoying eh, im gonna tinker around a bit i 'll let you know if i figure anything out, post back if you figure something out

---

