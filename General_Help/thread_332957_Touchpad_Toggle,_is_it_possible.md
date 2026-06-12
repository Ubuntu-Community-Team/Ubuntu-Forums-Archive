---
title: "Touchpad Toggle, is it possible?"
date: 2007-01-06
forum: General Help
---

### Post by Gen2ly on 2007-01-06
I can't find anything in the forums on how to do this.  I did try a slightly dated [one]("http://www.ubuntuforums.org/showthread.php?t=143095&highlight=turn+trackpad+off") .

Probably used in the previous Ubuntu Dapper.

When I did this Howto I restarted X and the desktop background was gone, transparency in panel and terminal were black, right click on desktop didn't work did nothing, and the toggle shortcut didn't work.  I was able to revert, thank you lord.

Here's what I did (diluted):

Add to /etc/X11/xorg.conf :

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option      	"SHMConfig" 		"on"
EndSection

downloaded [touchpad.py]("http://www.ubuntuforums.org/attachment.php?attachmentid=7043&d=1142321855")
sudo mv ~/Desktop/touchpad.py /usr/local/bin/
chmod 777 /usr/local/bin/touchpad.py
sudo visudo
and added this line
{user}     ALL = NOPASSWD: /usr/local/bin/touchpad.py
sudo apt-get install xbindkeys
sudo apt-get install xbindkeys-config
xbindkeys
xbindkeys-config

Under Edit on the right side:

Name: Touchpad Toggle
Key: Control+Shift + Num_Lock | m:0x5 + c:77
Action: /usr/local/bin/touchpad.py

---

Any ideas on what I need to do to toggle my touchpad on and off?

---

### Post by ecimon on 2007-01-06
Have you tried running 'synclient' manually?

If it works then you can use a script like this (works for me)
```

#!/bin/bash

        STATE=`synclient -l | grep TouchpadOff | awk '{ print $3 }'`;

        if [ "$STATE" == "0" ]; then
                synclient TouchpadOff=1;
        else
                synclient TouchpadOff=0;
        fi;

```

---

### Post by Gen2ly on 2007-01-06
synclient -l

returns:
Can't access shared memory area. SHMConfig disabled?

hmm, it is in my xorg.conf

---

### Post by ecimon on 2007-01-06
Have you added the "Synaptic Touchpad" to the ServerLayout? 

I've got something like this:
```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
        **InputDevice     "Synaptics Touchpad"**
EndSection

```

---

### Post by Gen2ly on 2007-01-06
You got quite the nose ecimon, no it wasn't there.  I restarted X and tried synclient again.

Ugh it didn't work agian.  In Xorg.0.log I got this when I searched synaptic:

(Note I couldn't seem to copy this info so I took a screenshot :)

[IMG]http://farm1.static.flickr.com/157/348516188_5a9a882515.jpg?v=0[/IMG]

---

### Post by ecimon on 2007-01-07
Check if kernel detectes the touchpad: If you
```

dmesg | less

``` 

Then you should see something like this:
```

[17179589.404000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04753/0x200000
[17179589.476000] input: SynPS/2 Synaptics TouchPad as /class/input/input2

```

I'm using the generic kernel so I'm not quite sure which driver you should use.  I suppose you could try **modprobe psmouse**.

I hope this helps :)

---

### Post by ecimon on 2007-01-07
This link might be helpful:
[http://www.users.bigpond.com/vkelim/SuSE_notes/node112.html](http://www.users.bigpond.com/vkelim/SuSE_notes/node112.html)

---

### Post by Gen2ly on 2007-01-07
found with dmesg | less

> [17179585.540000] input: Apple Computer Apple Internal Keyboard / Trackpad as /c
lass/input/input1
[17179585.540000] input: USB HID v1.11 Keyboard [Apple Computer Apple Internal K
eyboard / Trackpad] on usb-0000:00:1d.0-2
[17179585.544000] input: Apple Computer Apple Internal Keyboard / Trackpad as /c
lass/input/input2
[17179585.544000] input: USB HID v1.11 Mouse [Apple Computer Apple Internal Keyb
oard / Trackpad] on usb-0000:00:1d.0-2
[17179585.548000] input: Apple Computer Apple Internal Keyboard / Trackpad as /c
lass/input/input3
[17179585.548000] input: USB HID v1.11 Device [Apple Computer Apple Internal Key
board / Trackpad] on usb-0000:00:1d.0-2
[17179585.556000] hiddev96: USB HID v1.11 Device [Apple Computer, Inc. IR Receiv
er] on usb-0000:00:1d.2-2

hmm, definitely not Synaptic I'd say.

There would, I think, still be a way to toggle it on and off?

---

### Post by Gen2ly on 2007-01-10
Actually looks like support for Synaptics Touchpad for MacBooks just isn't in the kernal until 2.6.19.

Found this site (you'll need an able translator) that discusses putting it in the kernel:

[Ubuntu France]("http://doc.ubuntu-fr.org/installation/macbook")

---

### Post by Gen2ly on 2007-08-17
Thanks alot ecimon your script works nicely once the kernel has the ability added to it.

---

