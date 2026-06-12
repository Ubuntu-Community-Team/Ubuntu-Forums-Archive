---
title: "Re: HOWTO: Enable your Wacom Intous/Graphire Tablet with Pressure Sensitivity"
date: 2006-12-30
forum: General Help
---

### Post by threegremlins on 2006-12-30
I was given a wacom pen tablet over the season and couldn't wait to use it. I should know better, nothing is ever easy with Linux but, that's what makes it fun. I did a search using the words "wacom, graphire" and found **Re: HOWTO: Enable your Wacom Intous/Graphire Tablet with Pressure Sensitivity. **I read through it following the links and examples but nothing could get it working right. Then I came across a help page [https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting). It didn't actually help me but it put an idea in my head and I tried it out, well drop my jaw, it worked.  
Here's what I did; this is my  xorg.conf's pertinent section after following the instructions and it still wasn't working [B]

[SIZE=1]Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
  Option        "Device"        "/dev/input/event3"   # /dev/input/event
  Option        "Type"          "stylus"          # for USB
  Option        "USB"           "on" 
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
  Option        "Device"        "/dev/input/event3"   # /dev/input/event
  Option        "Type"          "eraser"              # for USB
  Option        "USB"           "on"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
  Option        "Device"        "/dev/input/event3"   # /dev/input/event
  Option        "Type"          "cursor"              # for USB
  Option        "USB"           "on"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection[/SIZE]

[SIZE=1]and this is after I had the brain spasm

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
  Option        "Device"        "/dev/input/event3"   # /dev/input/event
  Option        "Type"          "stylus"          # for USB
  Option        "USB"           "on" 
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
  Option        "PressCurve" "0,0,100,100"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
  Option        "Device"        "/dev/input/event3"   # /dev/input/event
  Option        "Type"          "eraser"              # for USB
  Option        "USB"           "on"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
  Option        "Device"        "/dev/input/event3"   # /dev/input/event
  Option        "Type"          "cursor"              # for USB
  Option        "USB"           "on"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Spot the difference look for the extra >#<, damn, the mouse that came with it even works too even though I would have been happy with just the pen.  As I said before  Linux is never easy, the wheel for whatever reason  scrolls in a reverse direction.   Hope this helps someone as much as everyone helped me to get this far. Thanks by the way and Happy New Year!
[/SIZE][/B]

---

### Post by threegremlins on 2006-12-31
Hey, here's me with egg on my face. After restarting next day, pen works differently and mouse too but, not the way their supposed to. Pen has to actually touch the tablet to move the cursor around, GIMP won't recognize it.
Harumph!
Later

---

### Post by nkkromhof on 2007-01-02
If you'd like to change the direction the scrollwheel scrolls then check out the small app that [this website]("http://foto-cs.de/blog/item/196") talks about, complete with instructions. I found it elsewhere on these forums.

As for the pen not working correctly anymore, this sometimes happens to me too, rebooting will **usually** fix the problem, if anyone knows what causes this, I'd love to hear!

The weird thing is that when this problem occurs for me, my mouse will not work either, reloading X by using CTRL-ALT-Backspace does not seem to fix it...

---

### Post by Tripmonkey_uk on 2007-01-02
> **nkkromhof said:**
> 
As for the pen not working correctly anymore, this sometimes happens to me too, rebooting will **usually** fix the problem, if anyone knows what causes this, I'd love to hear!


I've got the same problem after getting my Graphire3 tablet working with the pressure etc,

It seems that if I change my xorg.conf file from using **mice** to using **mouse1** (or any other number) the pressure works, but the computer becomes unstable. I can't use the tablet if I unplug the USB & then plug it back in either :(

If I keep the setting mice in my xorg.conf file, then the pressure doesn't work but the tablet has no problems what so ever. Even the USB hotplugging works.

It seems to be something to do with the mice/mouse settings.

I think it's because it assigns the same setting to the tablet everytime the computer is restarted (e.g. mouse1), but when ever I unplug the tablet & plug it back in, it tries to re-assign a different setting (e.g. mouse0, mouse2 or mouse3).

I think that this mix up is also why the tablet can be working fine one minute, & then just stop the next :(

---

### Post by nkkromhof on 2007-01-03
> **Tripmonkey_uk said:**
> 

If I keep the setting mice in my xorg.conf file, then the pressure doesn't work(

I tried this, and lost pressure sensitivity on the stylus, however the eraser still has pressure sensitivity... The stylus is in "relative" mode, the eraser is "absolute" (just forgot to change it). Now in Windows, "relative" mode is called Mouse Mode... which might make sense as far as changing the Mouse1/Mice setting goes, I'm just guessing here though.

I haven't tried using "absolute" mode on the stylus myself, I hate it and I don't need pressure sensitivity that bad. I also commented out the
```
 Option "PressCurve" "0,0,100,100"
``` in my xorg.conf. Because the first time I rebooted after the Mouse1/Mice change I HAD pressure sensitivity on the stylus, but it required a lot of force applied to it, so I changed the PressCurve option to a higher value (was just playing) and promptly had the old problem back after rebooting, so I commented the PressCurve option out again and, coincidence or not, next reboot it worked fine again.

I didn't have time to experiment more to see if this was a fluke...

---

### Post by threegremlins on 2007-01-04
Thanks for the link to fix the scroll direction I'll have to check it out. Since I was away I did some more hunting and came across a website that's helped. 

[http://www.i3s.unice.fr/~ol/success.html]("http://www.i3s.unice.fr/%7Eol/success.html")

Mind you I didn't follow all the advice it gave only the pertinent parts for my problem. It said to install a number of packages for an ATI card and mine is Nvidia but somewhere I read something like "contains useful 2d software" and I figured what the hell. In Synaptic I searched fglrx and came up with a number of packages. One, fglrx-kernal-source gave me some cause for concern so I cancelled it, ignored some of the others and selected only the ones with the Ubuntu logo.

linux restricted modules 2.6.17-10-386
xorg-driver-fglrx
xorg-driver-fglrx-dev

I changed the #-wacom.rules file earlier but checked to make sure it was the same since it was somewhat of an improvement over the original. I also copied the input Device section into my xorg.conf file, changing each
Option         "Device" "/dev/input/wacom"
to
Option         "Device" "/dev/input/event3"

I shut down the computer completely went and watched TV came back booted it up. It worked, to be sure I waited till the next day before I would call it a success. There's also some advice about not moving your usb plug around to other ports, it seems to confuse the configuration. 

I think I read somewhere  mice is  inclusive of the mouse if you still have it  plugged in and other devices. If you change it to point to a particular device it will only apply to that device and the others wont work. I'm not sure of this so don't think it's honto.

[LEFT]
[/LEFT]

---

### Post by Tripmonkey_uk on 2007-01-04
Cheers for that.
Ithink I need to do this part..

_Prepare for the /dev/input/wacom link_

In /etc/udev/rules.d/10-wacom.rules, add the following line:

KERNEL="event*", SYSFS{idVendor}="056a", NAME="input/%k", SYMLINK="input/wacom%e" 

Thus the drivers will find the Wacom tablet, whatever its /dev/input/eventX address is.

That should sort out one of my biggest problems.. I think? :-k

---

### Post by nkkromhof on 2007-01-05
> **Tripmonkey_uk said:**
> Cheers for that.
Ithink I need to do this part..

_Prepare for the /dev/input/wacom link_



I just tried this, everything's still working after the first reboot, crossing my fingers it'll stay that way :D If not I'll post it here, having to try two or three boots to get my tablet working was getting kind of old, so I'm hoping this took care of it!

---

### Post by KingCharles on 2007-02-08
Hi there guys.

Really grateful for all your tips. I got my wacom tablet working with no problem and with full sensitivity, mouse and all, on Edgy. Really want to squeeze the power out of Gimp (and inkscape which actually takes the wacom pretty good too :]  ).

I just want to mention, that you can add the following option to **/etc/X11/xorg.config** for better response between the X server and the wacom tablets:

```
Option    "Resolution"    "2540"
```

Now, the resolution depends on your model of wacom tablet (mine is an intuos2).
The resolution is specified in **lpi** (lines per inch).
I found the specs of mine at [wacom asia]("http://www.wacom-asia.com/products/intuos2/intuos2_spec.html"). I am pretty sure you can find all the other ones' specs there too.

---

