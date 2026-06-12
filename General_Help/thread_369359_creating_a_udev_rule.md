---
title: "creating a udev rule"
date: 2007-02-24
forum: General Help
---

### Post by cisforcojo on 2007-02-24
Hey all,

I'm having problems creating a udev rule.
I have an ALPS touchpad and have successfully disabled tapping but ONLY if I address the touchpad from the 'event' it's run on. If I plug in my USB mouse, the event changes and the tapping resumes. I'm trying to make a udev rule to handle this automatically but I'm failing.
Basically, I've created a file:

/etc/udev/rules.d/35-alps.rules

BUS="serio", SYSFS{description}="i8042 Aux-3 Port", KERNEL="event?", SYMLINK="input/alps"



in THEORY this creates a symlink that gets called by xorg.conf

Section "InputDevice"
	Identifier  "ALPS"
	Driver      "synaptics"
	Option	    "AlwaysCore"
	Option	    "Device" "/dev/input/alps"
	Option	    "Protocol" "event"
	Option	    "LeftEdge" "120"
	Option	    "RightEdge" "830"
	Option	    "TopEdge" "120"
	Option	    "BottomEdge" "650"
	Option	    "FingerLow" "14"
	Option	    "FingerHigh" "15"
	Option	    "MaxTapTime" "180"
	Option	    "MaxTapMove" "110"
	Option	    "ClickTime" "0"
	Option	    "EmulateMidButtonTime" "75"
	Option	    "VertScrollDelta" "10"
	Option	    "HorizScrollDelta" "0"
	Option	    "MinSpeed" "0.45"
	Option	    "MaxSpeed" "0.75"
	Option	    "AccelFactor" "0.020"
	Option	    "EdgeMotionMinSpeed" "200"
	Option	    "EdgeMotionMaxSpeed" "200"
	Option	    "UpDownScrolling" "1"
	Option	    "CircularScrolling" "0"
	Option	    "CircScrollDelta" "0.1"
	Option	    "CircScrollTrigger" "2"
	Option	    "SHMConfig" "true"
EndSection

and theory is where this story ends.

Any help is appreciated!

---

### Post by sisco311 on 2007-02-24
edgy
the symlink is in /dev/input/by-path/ :)

ex.:

ls -l /dev/input/by-path/
total 0
lrwxrwxrwx 1 root root 9 2007-02-24 18:47 pci-0000:00:0b.0-usb-0:3:1.0-event-mouse -> ../event2
lrwxrwxrwx 1 root root 9 2007-02-24 18:47 pci-0000:00:0b.0-usb-0:3:1.0-mouse -> ../mouse0
lrwxrwxrwx 1 root root 9 2007-02-24 18:46 pci-0000:04:09.0--event- -> ../event3
lrwxrwxrwx 1 root root 9 2007-02-24 18:47 platform-i8042-serio-1-event- -> ../event0
lrwxrwxrwx 1 root root 9 2007-02-24 18:47 platform-pcspkr-event- -> ../event1

---

### Post by cisforcojo on 2007-02-24
I think I'm not understanding your meaning. The event kept changing on the touchpad.
Sometime's it's event2 and sometimes event5 (depend on whether or not I'm using my USB mouse). I want Ubuntu to handle this automatically and make /dev/input/alps to symlink to whichever event that is. Then I can just use:

Device "/dev/input/alps"       in xorg.conf

---

### Post by sisco311 on 2007-02-25
/dev/input/by-path/**pci-0000:04:09.0--event-**  -> ../event3     <-- this is my remote control
after a reboot the event can change, but the symlink name remains the same
/dev/input/by-path/**pci-0000:04:09.0--event-** -> ../event2

so you don't need to create a a device "/dev/input/alps" in xorg.conf because is in /dev/input/by-path/

> I want Ubuntu to handle this automatically and make /dev/input/alps to symlink to whichever event that is. Then I can just use:

so ubuntu handle this automatically and make /dev/input/by-path/*name* to symlink to whichever event that is and you can  just use it.

---

### Post by sisco311 on 2007-02-25
65-persistent-input.rules :
```
SUBSYSTEM!="input",			GOTO="persistent_input_end"
ACTION!="add",				GOTO="persistent_input_end"
# ignore the mid-level drivers
KERNEL=="input[0-9]*",			GOTO="persistent_input_end"

# usb devices
BUS=="usb",				IMPORT{program}="usb_id -x"
BUS=="usb", SYSFS{bInterfaceClass}=="03", SYSFS{bInterfaceProtocol}=="01", \
					ENV{ID_CLASS}="kbd"
BUS=="usb", SYSFS{bInterfaceClass}=="03", SYSFS{bInterfaceProtocol}=="02", \
					ENV{ID_CLASS}="mouse"

# by-id links, generic and for the event devices
KERNEL=="mouse*", \
	ENV{ID_BUS}=="?*", ENV{ID_SERIAL}=="?*", ENV{ID_CLASS}=="?*", \
	SYMLINK+="input/by-id/$env{ID_BUS}-$env{ID_SERIAL}-$env{ID_CLASS}"
KERNEL=="event*", \
	ENV{ID_BUS}=="?*", ENV{ID_SERIAL}=="?*", ENV{ID_CLASS}=="?*", \
	SYMLINK+="input/by-id/$env{ID_BUS}-$env{ID_SERIAL}-event-$env{ID_CLASS}"

# by-path links
[B]IMPORT{program}="path_id %p"
KERNEL=="mouse*", ENV{ID_PATH}=="?*", \
	SYMLINK+="input/by-path/$env{ID_PATH}-$env{ID_CLASS}"
KERNEL=="event*", ENV{ID_PATH}=="?*", \
	SYMLINK+="input/by-path/$env{ID_PATH}-event-$env{ID_CLASS}"

LABEL="persistent_input_end"


```[/B]

---

### Post by cisforcojo on 2007-02-25
Huh... already had that as well. My udev file matches yours.

I tried changing the Device part in xorg.conf:

Section "InputDevice"
	Identifier  "ALPS"
	Driver      "synaptics"
	Option	    "AlwaysCore"
	Option	    "Device" "/dev/input/by-path/platform-i8042-serio-4-event-" 

But I'm still getting tapping problems. Sorry, I'm probably driving ya nuts. I'm just still getting familiar with Ubuntu. 

If I unplug my USB mouse and set the Device to the touchpad event, then it works. But otherwise, nothing.

---

### Post by sisco311 on 2007-02-25
[http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/]("http://ubuntu.wordpress.com/2005/11/15/fixing-my-alps-touchpad-with-the-synaptics-driver/")

---

### Post by cisforcojo on 2007-02-25
Yeah I've used that link before actually. I'm just going to leave the device section as
Device "/dev/input/event2" and say the hell with it when I'm not using a USB mouse.

Thanks for your help!

---

