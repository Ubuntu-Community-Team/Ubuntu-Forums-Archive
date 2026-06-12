---
title: "Mouse Acceleration and Speed woes"
date: 2019-11-23
forum: General Help
---

### Post by wallboy on 2019-11-23
I have just installed Xubuntu and I'm having some issues getting mouse acceleration disabled and mouse sensitivity correct. On other Linux distros, including regular Ubuntu, I have had good luck with either changing the profile to "flat" in the settings or using the following /etc/X11/xorg.conf.d/50-mouse-acceleration.conf file:

```
Section "InputClass"
    Identifier "My Mouse"
    MatchIsPointer "yes"
    Option "AccelerationProfile" "-1"
    Option "AccelerationScheme" "none"
    Option "AccelSpeed" "-1"
EndSection
```

Normally either of those changes would make my mouse feel exactly like it is in Windows (with 800 DPI set in the mouse firmware and Windows default sens of 6). However the sensitivity feels more closer to 200 DPI for some reason in Xubuntu.

I also tried installing libinput-tools and changing the above code to: 

```
Section "InputClass"
    Identifier "My Mouse"
    Driver "libinput"
    MatchIsPointer "yes"
    Option "AccelProfile" "flat"
    Option "AccelSpeed" "0"
EndSection
```

But this code makes my mouse speed almost completely standstill. Like 1 meter of mouse movement = 1cm on the screen slow.

I then tried to play around with the Transformation Matrix settings of the mouse and changing it from the default of "1 0 0 0 1 0 0 0 1" to "3 0 0 0 3 0 0 0 1" and this ALMOST gets the mouse speed to where I want it without any acceleration, though these changes in the transformation matrix have the side effect of when moving your mouse slowly it jumps many pixels. Like the setting is interpolating a higher mouse speed.

Here is my xinput properties of how I currently have my mouse set:

```
Device 'ROCCAT ROCCAT Kone Aimo Mouse':
    Device Enabled (155):    1
    Coordinate Transformation Matrix (157):    3.000000, 0.000000, 0.000000, 0.000000, 3.000000, 0.000000, 0.000000, 0.000000, 1.000000
    libinput Natural Scrolling Enabled (289):    0
    libinput Natural Scrolling Enabled Default (290):    0
    libinput Scroll Methods Available (291):    0, 0, 1
    libinput Scroll Method Enabled (292):    0, 0, 0
    libinput Scroll Method Enabled Default (293):    0, 0, 0
    libinput Button Scrolling Button (294):    2
    libinput Button Scrolling Button Default (295):    2
    libinput Middle Emulation Enabled (296):    0
    libinput Middle Emulation Enabled Default (297):    0
    libinput Accel Speed (298):    -1.000000
    libinput Accel Speed Default (299):    0.000000
    libinput Accel Profiles Available (300):    1, 1
    libinput Accel Profile Enabled (301):    1, 0
    libinput Accel Profile Enabled Default (302):    1, 0
    libinput Left Handed Enabled (303):    0
    libinput Left Handed Enabled Default (304):    0
    libinput Send Events Modes Available (274):    1, 0
    libinput Send Events Mode Enabled (275):    0, 0
    libinput Send Events Mode Enabled Default (276):    0, 0
    Device Node (277):    "/dev/input/event2"
    Device Product ID (278):    7805, 11815
    libinput Drag Lock Buttons (305):    <no items>
    libinput Horizontal Scroll Enabled (306):    1

```

I'm not sure why I'm struggling getting the mouse speed to work correctly on Xubuntu. Not sure if it's a XFCE thing that's causing this? Is the "Mouse and touchpad" settings somehow overriding xinput?

Any help would be appreciated,

Thanks

---

### Post by wallboy on 2019-11-24
Alright, I've solved the issue. So basically it seems what's happening is that the "AccelSpeed" Option in the .conf file is being overridden by the Acceleration setting in the "Mouse and touchpad" xfce GUI. For my particular mouse, my AccelSpeed needs to be 0.0 and I found out if I set the Acceleration to 5.0 in the GUI, this corresponds to a libinput AccelSpeed of 0.0.

Still curious though if anyone knows which configuration file would be overriding my /etc/X11/xorg.conf.d/50-mouse-acceleration.conf file?

---

### Post by Holger_Gehrke on 2019-11-24
If you're running XFCE, then the settings for pointing devices are stored in xfconf in the channel pointers.
```

xfconf-query --channel pointers --list

```
will show all the property names for pointing devices. 

The actual file that contains these settings should be ~/.config/xfce4/xfconf/xfce-perchannel-xml/.

Holger

---

### Post by sgage on 2019-11-24
I have had problems with mouse speed in several DE's. I tend to use MATE most of the time. Anyway, the workaround I've found effective is to create a shell script (I cleverly call it 'libinput.sh') thus:

```
#! /bin/bash
xinput --set-prop 10 'libinput Accel Speed' -0.80
```

The speed setting (-0.80 in this case) can be set to whatever works for you. -0.90 is slower, -0.70 is faster, etc.

I keep the script in my home directory. Then I added an item to my startup programs (which in a fit of creativity I named 'libinput'):

```
/home/sgage/libinput.sh
```

The device number for --set-prop can be determined by a simple 'xinput' command:

```
~$ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PixArt HP USB Optical Mouse             	id=10	[slave  pointer  (2)]
&#9116;   &#8627; HP USB Multimedia Keyboard              	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HP USB Multimedia Keyboard              	id=11	[slave  keyboard (3)]
    &#8627; HP WMI hotkeys                          	id=13	[slave  keyboard (3)]
    &#8627; HP USB Multimedia Keyboard    
```

So I could see that my mouse was id=10. You may have to apt install xinput if it's not already there. 

This technique has worked on any system I've tried it on. If you change things on your computer, move connectors around, etc., you may have to check the mouse id again. I had a version of this script with logic to parse the xinput output and automatically set the proper id, and it sort of worked, but I like simple. Besides, I sit here at my desktop most of the time, and nothing much changes. 8-)

---

### Post by Holger_Gehrke on 2019-11-24
If you like simple, then simply using the name instead of the id would be better than trying to parse the output of xinput.
```

xinput --set-prop 'PixArt HP USB Optical Mouse' 'libinput Accel Speed' -0.80

```
The id is not guaranteed to be stable from one session to the next while the name is.

Holger

---

### Post by sgage on 2019-11-24
> **Holger_Gehrke said:**
> If you like simple, then simply using the name instead of the id would be better than trying to parse the output of xinput.
```

xinput --set-prop 'PixArt HP USB Optical Mouse' 'libinput Accel Speed' -0.80

```
The id is not guaranteed to be stable from one session to the next while the name is.

Holger

I didn't know you could use the name - thanks for the tip!

---

