---
title: "Middle click no longer works"
date: 2008-06-29
forum: General Help
---

### Post by NickEvans on 2008-06-29
Recently, my middle click functionality has stopped working. I can scroll up and down, but when I select text and middle click somewhere else, it no longer pastes. Also, I can not middle click on a link to open a new tab in Firefox. This issue affects all applications, as far as I can tell. 

In case you need it:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
	Option		"Emulate3Buttons"	"true"
EndSection

```

Thanks in advance.

---

### Post by manfer on 2008-06-29
Please post which is your mouse. Or at least the kind of mice, optical or not, button numbers...

---

### Post by manfer on 2008-06-29
Option Emulate3Buttons boolean
    Enable/disable the emulation of the third (middle) mouse button for mice which only have two physical buttons. The third button is emulated by pressing both buttons simultaneously. Default: off

I think you don't need that on. Comment that line and try.

---

### Post by NickEvans on 2008-06-30
I tried commenting it and also setting it to false.
I saw in another post that xev shows if X is getting input from event devices. When I middle click in the window, nothing happens at all, but I get button press and button release events for scrolling and left/right clicking. 

Any other ideas?

EDIT> The mouse is a Logitech RX300

---

### Post by manfer on 2008-07-01
Try this one:

First let's determine which is the input device that handles your mouse events. Type:

prompt:~$ **cat /proc/bus/input/devices**

and look for the mouse. I show you and example from my mouse so you can look for yours in the output of that command:

I: Bus=0003 Vendor=046d Product=c00c Version=0110
N: Name="Logitech USB Optical **Mouse**"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input2
U: Uniq=
H: Handlers=mouse1 **event2** 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
B: MSC=10

In my case it is event2, but more probably yours would be event1. When you had research that data, edit /etc/X11/xorg.conf:

```

Section "InputDevice"
   Identifier  "Configured Mouse"
   Driver      "evdev"
   Option      "Device"   "/dev/input/event1"
   Option      "CorePointer"
EndSection

```

restart X (close session and login again if you don't know any other method) and in a terminal type this command:

prompt:~$ **xmodmap -e "pointer = 1 2 3 4 5 7 6 8 9 10 11 12"**

Try with that, if second mouse button is not working as expected, try instead:

prompt:~$ **xmodmap -e "pointer = 1 3 2 4 5 7 6 8 9 10 11 12"**

---

