---
title: "Question about mouse/keyboard diagnostics"
date: 2015-09-17
forum: General Help
---

### Post by andrew261 on 2015-09-17
I'm attempting to get Xorg properly running on my new Ubuntu hardware, but I have yet to get either mouse or keyboard input working properly.  There may be a larger problem with my setup because I'm not sure how to go about configuring the devices in the xorg conf file.

When I plug in my mouse, for example, I only see these new devices show up in /dev/

/dev/char/189:12
/dev/bus/usb/001/013

And this when using lsusb:

Bus 001 Device 013: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse

And with xinput list

&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]

Does this seem correct, or should there be something else in /dev/ to indicate I have a valid mouse plugged in?

---

### Post by tgalati4 on 2015-09-18
Welcome to the forums.

Normally mouse and keyboard devices are plug-and-play, no configuration required.

Unplug the mouse and keyboard.

Post the entire:

```
xinput list
```

For a typical laptop with a trackpad, it will look like:

> tgalati4@Mint17 ~/Desktop $ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Acer CrystalEye webcam                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]


Now, plug in the mouse only and:

```
xinput list
```

Now, plug in the keyboard:

```
xinput list
```

What version of Ubuntu?  What is your keyboard make and model?  I presume your mouse is a Logitech Optical Wheel Mouse.  Try using different mice and keyboards and find something that works.  Have you made any other xorg.conf changes?  If so, rename the xorg.conf file to xorg.bad and reboot.
Modern distros don't need xorg.conf unless you are doing something very specific.

---

