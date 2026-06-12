---
title: "HIDDEV Device Number Assignments"
date: 2008-04-21
forum: General Help
---

### Post by dugald on 2008-04-21
I am trying to set up a touchscreen terminal running Ubuntu.

The touchscreen works fine.  However, if I plug in a wireless mouse before booting, I lose the functionality of the touchscreen.  Its fine if I boot and *then* plug in the wireless mouse.

The xorg.conf device section for the touchscreen includes an 
**Option         "Device"        "/dev/usb/hiddev0"** 
line.  If I change it to **hiddev1** then it works when I boot with the mouse already plugged in, but doesn't if I unplug the wireless mouse before booting.

I checked **dmesg** and it shows that the wireless mouse is discovered first (no matter what USB port it is on) and gets assigned as hiddev96 and then the touchscreen is discovered and assigned to hiddev97.  If there is no mouse, the touchscreen is hiddev96.

The problem is clear, but the solution isn't.  I need the touchscreen to work regardless of whether the wireless mouse is plugged in or not.  Any ideas? :confused:

---

### Post by justleen on 2008-04-21
you need to dive intoyout udev rules, to make sure the device always gets the same name. Udev is what takes care of this.

---

### Post by ryanhaigh on 2008-04-21
[http://gentoo-wiki.com/HOWTO_Customizing_UDEV](http://gentoo-wiki.com/HOWTO_Customizing_UDEV) unfortunately it doesn't have anything about changing things for mice although it did remind me about something that maybe useful.

One of the MANY times I tried to configure my logitech mouse I made modifications to xorg.conf which involved inserting information specific to that hardware. Im guessing that information would be sufficient to ensure that your system uses the correct device. Here is an extract from a blog that I used:
> Section &#8220;InputDevice&#8221;
Identifier &#8220;Mouse[1]&#8221;
Driver &#8220;mouse&#8221;
Option &#8220;Protocol&#8221; &#8220;explorerps/2&#8243;
[B]Option &#8220;Dev Name&#8221; &#8220;PS2++ Logitech MX Mouse&#8221; # cat /proc/bus/input/devices
Option &#8220;Dev Phys&#8221; &#8220;isa0060/serio1/input0&#8243; # cat /proc/bus/input/devices[/B]
Option &#8220;Device&#8221; &#8220;/dev/input/mice&#8221;
Option &#8220;Buttons&#8221; &#8220;10&#8243;
Option &#8220;ZAxisMapping&#8221; &#8220;4 5&#8243;
Option &#8220;ButtonMapping&#8221; &#8220;1 2 3 6 7&#8243;
Option &#8220;Resolution&#8221; &#8220;800&#8243;
Option &#8220;Emulate3Buttons&#8221; &#8220;no&#8221;
EndSection


This thread has similar info: [http://ubuntuforums.org/showthread.php?t=399374](http://ubuntuforums.org/showthread.php?t=399374)

Hope it is useful, post back if you need some help.

---

### Post by dugald on 2008-04-21
Thanks guys.  I looked into udev a bit more and found this page:

[http://www.harbaum.org/till/cnc/cx-t100/index.shtml]("http://www.harbaum.org/till/cnc/cx-t100/index.shtml")

which seems to be exactly what I am looking for.  :)

---

