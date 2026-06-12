---
title: "Ubuntu 14.04 missing Synaptics Touchpad Utility"
date: 2014-04-18
forum: General Help
---

### Post by tecknomage on 2014-04-18
My previous version of **Ubuntu 13.10** allowed me to install a Synamptic Touchpad tool that had a setting to **disable my ThinkPad touchpad_ when my mouse was connected_**.

In the **Starup Applications** list it is [Synaptiks Ttouchpad]

After upgarde this utility is missing from **Ubuntu 14.04** and not in **Ubuntu Software Store**.  How can I get it back :confused:

Note that in **Ubuntu 13.10** I got the utility_ from the store_.

---

### Post by caver12 on 2014-04-18
Do this;
sudo apt-get update
sudo apt-get install synaptics

---

### Post by Navneet_Kumar on 2014-04-18
sudo apt-get install synaptiks

Hope this helps

---

### Post by russomarco on 2014-04-26
As you can see on the [package page on launchpad]("https://launchpad.net/ubuntu/+source/synaptiks"), synaptiks has been developed until Ubuntu 13.10. I tried installing the package for 13.10 on 14.04 but it conflicts with the default Ubuntu Mouse & Touchpad utility. 

A package for 14.04 could be made available in the future, but I'm not sure about that. 

Since I was missing this utility too, and the default one is missing some customization options, in the meantime I'm using **Gpointing device settings**. It is pretty good and it has an option to disable the touchpad if a mouse is connected. You can find it in the Software Center. Hope it helps! :)

---

### Post by hut_mit on 2014-04-28
you can try 2 finger touch your touchpad.

---

### Post by caver12 on 2014-04-28
If you would do some research you would find that synaptiks is no longer being maintained. That is probably why it is not in the 14.04 repositories.I thinkIpointed you to that information before elsehttps://github.com/synaptiks/synaptiks ware.
look at- [https://github.com/synaptiks/synaptiks](https://github.com/synaptiks/synaptiks)

---

### Post by russomarco on 2014-05-05
**UPDATE:** **Gpointing device settings** doesn't save settings after reboot/shutdown and I couldn't find a solution for it. So, I had to use **xinput** from the terminal. This is how you do it:

1) Check the name of your device:
```
xinput list
```
2) See available options for your device:
```
xinput list-props "Your Device Name"
```
3) Edit settings (to make settings consistent after reboot/shutdown just **add this command to Startup Applications**):
```
xinput set-prop "Your Device Name" "Option Name" "Value"
```
Here is an example command I used to activate locked drags in my touchpad:
```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Locked Drags" 1
```
To activate/change another option just look for it in your device available options and play with them until you get the desired result, then add the command to Startup Applications and you're done! Hope it helps! : )

---

### Post by pretty_whistle on 2014-05-05
If the OP still has this issue here's the fix (I did it on mine):

Go into applications, settings, and find "mouse and touchpad".  Select the touchpad from the drop down list and uncheck it to disable it.

That's it.  This will solve it.  Synaptics wont install on 14.04 but this will work instead.

Good luck.

---

### Post by russomarco on 2014-05-07
**SECOND UPDATE:** Instead of the terminal method explained above, if you need just some simple tweaks like **disabling touchpad while mouse is connected**, you can use **touchpad-indicator**:

```
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
```

---

### Post by walterorlin on 2014-05-08
I think there is another method to turn it on and off is synclinet touchpadoff=1 to a keybinding in ~/.config/openbox and synclient toucpadoff=0 to another key or make a script that makes one act as a toggle button.

---

### Post by jean noel on 2014-05-24
Just installed 14.04 on my laptop, with the same touchpad scrolling not working. Tried the "two finger touch". Worked. Pretty good advice
Regards

---

### Post by superian on 2014-05-25
> **russomarco said:**
> **S**if you need just some simple tweaks like **disabling touchpad while mouse is connected**, you can use **touchpad-indicator**:

The one I notice it is missing is disabling tap to click.

---

### Post by wachin-id on 2014-11-12
I buy a Logitech Keyboard Touchpad K400r ([http://www.logitech.com/es-es/product/wireless-touch-keyboard-k400r](http://www.logitech.com/es-es/product/wireless-touch-keyboard-k400r)). Working, but I alway use a command on the terminal with my laptop touchpad Dell Inspiron 1750:

```
synclient LockedDrags=1
```

but not working on logitech.

Now I do this:

```
wachin@wachin-id:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:4024    id=10    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; Integrated_Webcam_1.3M                      id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=13    [slave  keyboard (3)]

```

I see that Logitech is pressent, now in this moment I am writing with them. Next I put on the terminal:

```
wachin@wachin-id:~$ xinput list-props "Logitech Unifying Device. Wireless PID:4024"
Device 'Logitech Unifying Device. Wireless PID:4024':
    Device Enabled (133):    1
    Coordinate Transformation Matrix (135):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (265):    0
    Device Accel Constant Deceleration (266):    1.000000
    Device Accel Adaptive Deceleration (267):    1.000000
    Device Accel Velocity Scaling (268):    10.000000
    Device Product ID (252):    1133, 50475
    Device Node (253):    "/dev/input/event4"
    Evdev Axis Inversion (269):    0, 0
    Evdev Axes Swap (271):    0
    Axis Labels (272):    "Rel X" (143), "Rel Y" (144), "Rel Horiz Wheel" (262), "Rel Dial" (263), "Rel Vert Wheel" (264)
    Button Labels (273):    "Button Left" (136), "Button Middle" (137), "Button Right" (138), "Button Wheel Up" (139), "Button Wheel Down" (140), "Button Horiz Wheel Left" (141), "Button Horiz Wheel Right" (142), "Button Side" (257), "Button Extra" (258), "Button Forward" (259), "Button Back" (260), "Button Task" (261), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255)
    Evdev Middle Button Emulation (274):    0
    Evdev Middle Button Timeout (275):    50
    Evdev Third Button Emulation (276):    0
    Evdev Third Button Emulation Timeout (277):    1000
    Evdev Third Button Emulation Button (278):    3
    Evdev Third Button Emulation Threshold (279):    20
    Evdev Wheel Emulation (280):    0
    Evdev Wheel Emulation Axes (281):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (282):    10
    Evdev Wheel Emulation Timeout (283):    200
    Evdev Wheel Emulation Button (284):    4
    Evdev Drag Lock Buttons (285):    0

```

I don't know the tipe of input for this device. Now I put on the terminal:

```
wachin@wachin-id:~$ xinput list-props "Logitech Unifying Device. Wireless PID:4024" "Synaptics Locked Drags" 1
Device 'Logitech Unifying Device. Wireless PID:4024':
    Device Enabled (133):    1
    Coordinate Transformation Matrix (135):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (265):    0
    Device Accel Constant Deceleration (266):    1.000000
    Device Accel Adaptive Deceleration (267):    1.000000
    Device Accel Velocity Scaling (268):    10.000000
    Device Product ID (252):    1133, 50475
    Device Node (253):    "/dev/input/event4"
    Evdev Axis Inversion (269):    0, 0
    Evdev Axes Swap (271):    0
    Axis Labels (272):    "Rel X" (143), "Rel Y" (144), "Rel Horiz Wheel" (262), "Rel Dial" (263), "Rel Vert Wheel" (264)
    Button Labels (273):    "Button Left" (136), "Button Middle" (137), "Button Right" (138), "Button Wheel Up" (139), "Button Wheel Down" (140), "Button Horiz Wheel Left" (141), "Button Horiz Wheel Right" (142), "Button Side" (257), "Button Extra" (258), "Button Forward" (259), "Button Back" (260), "Button Task" (261), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255), "Button Unknown" (255)
    Evdev Middle Button Emulation (274):    0
    Evdev Middle Button Timeout (275):    50
    Evdev Third Button Emulation (276):    0
    Evdev Third Button Emulation Timeout (277):    1000
    Evdev Third Button Emulation Button (278):    3
    Evdev Third Button Emulation Threshold (279):    20
    Evdev Wheel Emulation (280):    0
    Evdev Wheel Emulation Axes (281):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (282):    10
    Evdev Wheel Emulation Timeout (283):    200
    Evdev Wheel Emulation Button (284):    4
    Evdev Drag Lock Buttons (285):    0
unable to find device Synaptics Locked Drags
unable to find device 1

```

But is not active the feature LockedDrags on mi external touchpad logitech. Do you can help me

---

