---
title: "[SOLVED] Mouse wheelscroll problems"
date: 2008-06-30
forum: General Help
---

### Post by AwaZ on 2008-06-30
Installed Ubuntu yesterday for the first time, and in the beginning i had a problem with the wheel click, searched some around here and got that fixed. So everything worked fine yesterday. 

But when I turned on the computer today, I got this new problem.. Scrolling down is inverted (I have to scroll the wheel up to go down) and I can't use the wheel to scroll up at all..

---

### Post by NT4usB on 2008-06-30
First, how did you 'fix' it originally? ButtonMapping?
post the InputDevice section for your mouse from your xorg.conf.
```
cat /etc/X11/xorg.conf >~/xorg.txt
``` will make a textfile in your home folder of xorg.conf. You can copy/paste from there.

---

### Post by AwaZ on 2008-06-30
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
	Option	    "Buttons"	"5"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option      "Emulate3Buttons"     "on"
        Option      "Emulate3TimeOut"     "50"
        Option      "EmulateWheel"        "on"
        Option      "EmulateWheelTimeOut" "200"
        Option      "EmulateWheelButton"  "2"
        Option      "YAxisMapping"        "4 5"
        Option      "XAxisMapping"        "6 7"
        Option      "ZAxisMapping"        "5 6"
EndSection
```

---

### Post by manfer on 2008-06-30
That looks really strange. Which is your mouse model?

I don't understand. If the mouse has 5 buttons why you need Emulate3Buttons and Emulate3Timeout?

[I]Option Emulate3Buttons boolean
    Enable/disable the emulation of the third (middle) mouse button for mice which only have two physical buttons. The third button is emulated by pressing both buttons simultaneously. Default: off 

Option Emulate3Timeout integer
    Sets the timeout (in milliseconds) that the driver waits before deciding if two buttons where pressed "simultaneously" when 3 button emulation is enabled. Default: 50. [/I] 


If it has wheel, are EmulateWheel, EmulateWheelTimeOut, EmulateWheelButton, XAxisMapping, YAxisMapping, ZAxisMapping needed?

[I]Option EmulateWheel boolean
    Enable/disable "wheel" emulation. Wheel emulation means emulating button press/release events when the mouse is moved while a specific real button is pressed. Wheel button events (typically buttons 4 and 5) are usually used for scrolling. Wheel emulation is useful for getting wheel-like behaviour with trackballs. It can also be useful for mice with 4 or more buttons but no wheel. See the description of the EmulateWheelButton, EmulateWheelInertia, XAxisMapping, and YAxisMapping options below. Default: off.

Option EmulateWheelButton integer
    Specifies which button must be held down to enable wheel emulation mode. While this button is down, X and/or Y pointer movement will generate button press/release events as specified for the XAxisMapping and YAxisMapping settings. Default: 4. 

Option EmulateWheelTimeout integer
    Specifies the time in milliseconds the EmulateWheelButton must be pressed before wheel emulation is started. If the EmulateWheelButton is released before this timeout, the original button press/release event is sent. Default: 200. 

Option XAxisMapping N1 N2
    Specifies which buttons are mapped to motion in the X direction in wheel emulation mode. Button number N1 is mapped to the negative X axis motion and button number N2 is mapped to the positive X axis motion. Default: no mapping. 

Option YAxisMapping N1 N2
    Specifies which buttons are mapped to motion in the Y direction in wheel emulation mode. Button number N1 is mapped to the negative Y axis motion and button number N2 is mapped to the positive Y axis motion. Default: no mapping. 

Option ZAxisMapping X
Option ZAxisMapping Y
Option ZAxisMapping N1 N2

Option ZAxisMapping N1 N2 N3 N4
    Set the mapping for the Z axis (wheel) motion to buttons or another axis (X or Y). Button number N1 is mapped to the negative Z axis motion and button number N2 is mapped to the positive Z axis motion. For mice with two wheels, four button numbers can be specified, with the negative and positive motion of the second wheel mapped respectively to buttons number N3 and N4. Note that the protocols for mice with one and two wheels can be different and the driver may not be able to autodetect it. Default: "4 5". [/I]

I think all those are unnecessary but please post mouse model.

---

### Post by NT4usB on 2008-06-30
Type:```
xev
``` in a terminal and see what each motion returns.
Z should be 4 5

You can move the numbers around until you get the desired result.

Here's mine for reference, Mx310, no X or Y.(Ignore the ButtonMapping. I use it to get the thumb button to act as middle click)```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 6 3 2 4 5"
        Option          "Resolution"            "100"
EndSection
```

---

### Post by AwaZ on 2008-06-30
I just copy / pasted the InputDevice from another topic here, where some guy had the same problem as me.. 

I got a Creative OMC905
but have also tried with a Logitech mouse, and getting the same problem.

I find it strange how it worked fine right after making the changes, but wouldn't work the day after.

---

### Post by AwaZ on 2008-06-30
> **NT4usB said:**
> Type:```
xev
``` in a terminal and see what each motion returns.

```
ButtonPress event, serial 33, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 6375094, (174,101), root:(675,530),
    state 0x10, button 5, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 6375094, (174,101), root:(675,530),
    state 0x1010, button 5, same_screen YES

ButtonPress event, serial 33, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 6378542, (174,101), root:(675,530),
    state 0x10, button 6, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 6378542, (174,101), root:(675,530),
    state 0x10, button 6, same_screen YES

```

Not sure if that's what you wanted. button 5 is when I scrolled up, button 6 is when I scrolled down

---

### Post by NT4usB on 2008-06-30
It's doing what xorg is telling it to do. Since 6 is not UP, it's not going up though. 5 is UP so that's what it does.
I don't find any (English) references to your mouse so I can't see the button layout.
Does it have X and Y buttons/wheel?
Can you find a motion that returns a 4 in xev? That should also be the motion that scrolls up.
Edit your xorg.conf, change: 
Option          "ZAxisMapping"          "4 5"
and it will scroll up and down. 
Comment out the X and Y mappings for now.
To get X and Y to work, you'll probably have to use ButtonMapping but without knowing all the buttons it's hard to guess what to set up.
There are probably ways to change how Ubuntu reacts to 5 and 6, to make them the Up and Down, but I don't know how to do that.

---

### Post by AwaZ on 2008-06-30
There is no button 4, I tried clicking all buttons, and making combinations. 

I have a 5 button mouse (left click, right click, wheel + scrolling), not sure what X and Y buttons are. 

Removed X and Y from xorg, and changed Z to 4 5, didn't fix it, tried different combos too on Z, but none fixed it.

---

### Post by NT4usB on 2008-06-30
Post your new xorg section.
Restart x (Ctrl+Alt+Backspace)
Does xev show 4 and 5 when you scroll up and down?

---

### Post by AwaZ on 2008-06-30
Searched some more on the net, and found a site 2 seconds before you posted :p

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "vmmouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Buttons" "5"
Option "ZAxisMapping" "4 5"
EndSection
```

It works fine now, didn't know that i had to restart x, so that could have been the problem earlier when you tried to help, sorry for the bother and thanks=)

---

### Post by NT4usB on 2008-06-30
Cool.
I didn't know if you had to restart x either but it was worth a try *g*.
Be sure to mark the post solved using the Forum tools above.

---

