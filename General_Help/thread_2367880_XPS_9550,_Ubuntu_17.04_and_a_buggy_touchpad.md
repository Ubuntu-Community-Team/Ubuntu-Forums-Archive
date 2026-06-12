---
title: "XPS 9550, Ubuntu 17.04 and a buggy touchpad"
date: 2017-08-04
forum: General Help
---

### Post by knerlington on 2017-08-04
Just after login the touchpad works great. As precise and responsive as can be, all gestures that are supposed to work works. Tapping, scrolling. The basics really. After a while though the "tap to click" and scrolling stops working. The mouse pointer remains active and I can still use the physical clicks.
The issue doesn't happen in Windows so I know it's not a hardware issue.

Usually I have two touchpads listed if I run "xinput list", but having those two listed there causes problems with palm detection (it doesn't always work or stops working after a while.)
To fix this I added the following section to "51-synaptics-quirks.conf" under /usr/share/X11/xorg.conf.d

```
# Disable generic Synaptics device, as we're using
# "DLL0704:01 06CB:76AE Touchpad"
# Having multiple touchpad devices running confuses syndaemon
Section "InputClass"
        Identifier "SynPS/2 Synaptics TouchPad"
        MatchProduct "SynPS/2 Synaptics TouchPad"
        MatchIsTouchpad "on"
        MatchOS "Linux"
        MatchDevicePath "/dev/input/event*"
        Option "Ignore" "on"
EndSection
```

06CB:76AE Touchpad is the first one listed in xinput, but without above section it also lists the Synaptics one.
I am supposed to use the 06CB:76AE Touchpad and only that one right? 

Tap to click is always enabled in the system settings under mouse and touchpad. What could cause it to stop listening to touch events? Highly annoying having to combat either the palm detection not working and now this.
I use the following command at startup to set my own palm detection idle time before listening to key presses again syndaemon -i .5 -K -R -t -d.

---

### Post by knerlington on 2017-08-08
UPDATE:
Right after login I have the following touchpads being detected according to xinput.
During this time the automatically started process "syndaemon" is supposed to disable the touchpad tapping while typing,  but it does not work.
Killing it and manually starting it again with the -v (messages) parameter shows that syndaemon is responding to the event of my keys being pressed. It prints "enabled/disabled" all the time. Still though something is stopping the tapping function from actually being disabled. What could cause this? To me this issue really makes using Ubuntu unbearable and pretty much impossible since I prefer to actually use my touchpad. I am running it on a laptop after all. Desperate to get some help here. 


&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; DLL06E4:01 06CB:7A13 Touchpad           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; Integrated_Webcam_HD                    	id=11	[slave  keyboard (3)]
    &#8627; Intel HID events                        	id=13	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=14	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys 

Concatenating /proc/bus/input/devices results in two entries for a touchpad: 
Going by what's written in DebuggingTouchpadDetection on the wiki having entries here rules out the kernel being the issue and that HAL might be where the problem lies.

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse0 event7 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=660800011000003

I: Bus=0018 Vendor=06cb Product=7a13 Version=0100
N: Name="DLL06E4:01 06CB:7A13 Touchpad"
P: Phys=i2c-DLL06E4:01
S: Sysfs=/devices/pci0000:00/0000:00:15.1/i2c_designware.1/i2c-7/i2c-DLL06E4:01/0018:06CB:7A13.0001/input/input20
U: Uniq=
H: Handlers=mouse1 event17 
B: PROP=5
B: EV=b
B: KEY=e520 10000 0 0 0 0
B: ABS=260800000000003

Now I feel lost. Don't know which entries I should see under xinput or in /proc/bus/input/devices.
I want palm detection and the ability to disable to keyboard while typing to work.

---

