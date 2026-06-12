---
title: "Total lock up"
date: 2007-08-04
forum: General Help
---

### Post by SWoodhall on 2007-08-04
Hi Guys

I've been using ubuntu for a few months now and really love it, but I have a problem that is frequently causing me to boot back to my windows partition. Ubuntu FF completely locks up on me, the mouse pointer will still move, but I get total keyboard lockout so I can't even restart X. It seems to me that this always seems to happen when I am using gmail in firefox, but it could be a red herring.

I wonder if someone might be able to point me in the right direction to track down the cause. I have looked in the syslogs but can't find anything that looks helpful. I am very new to Nix systems. 

At risk of being mobbed (:D) my windows partition on the same hardware does not suffer similar issues.

Cheers in advance!

---

### Post by apswartz on 2007-08-04
give us the contents of your /var/log/Xorg.0.log file. You can attach it using the Manage Attachments button below Additional Options, and/or reproduce the relevant portions in a reply.

---

### Post by SWoodhall on 2007-08-04
Thanks for the response. I had a lot of problems posting this as Ubuntu locked up on me 3 times while trying to do it! All times I was in gmail, so I still wonder if this is somehow the cause.

Unfortunately the forum won't allow me to upload the full log file as it is too large (50k or so) and if I try to add it to this reply it tells me that it has 24 images in it which is above the limit. Bearing in mind I am copying this straight from gedit I am confused!

---

### Post by apswartz on 2007-08-04
just give us the last 50 lines

---

### Post by SWoodhall on 2007-08-04
thx ok here we go :


(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
AUDIT: Sat Aug  4 21:54:37 2007: 5004 X: client 4 rejected from local host (uid 1000)
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1

---

### Post by apswartz on 2007-08-04
From you error, and looking at this thread...
[http://ubuntuforums.org/showthread.php?t=193670](http://ubuntuforums.org/showthread.php?t=193670)
it looks like you will need to reinstall your video driver.

Perhaps reconfiguring X will help...
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by SWoodhall on 2007-08-05
Thanks. I'll give it a try.

---

### Post by SWoodhall on 2007-08-05
Thanks apswartz. I have reconfigured X to use fglrx as the driver and I don't seem to have the problem any more. Unfortunately in doing that I now cannot use compiz or beryl, which I was previously working. Not to worry I will do some more research into that problem.

---

