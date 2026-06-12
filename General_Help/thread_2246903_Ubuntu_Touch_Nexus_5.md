---
title: "Ubuntu Touch Nexus 5"
date: 2014-10-04
forum: General Help
---

### Post by mark.hilt1 on 2014-10-04
Hello so first off I am sorry if this is the wrong section. I  have installed the ubuntu touch on my nexus 5 and I am wondering is the nexus 5 even back in development yet or is it canceled for good because I would love to have a ubuntu touch phone if you can get back to me I would greatly apreciate it.

---

### Post by ian-weisser on 2014-10-04
The list of currently-supported, obsolete, and somebody-ported-it devices is at [https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

---

### Post by mark.hilt1 on 2014-10-10
I see there that Nexus 5 is a working port without bluetooth so why is it not working? it just does not detect my sim card yet any android rom does

---

### Post by grahammechanical on 2014-10-10
> [COLOR=#000000]why is it not working?[/COLOR]

Because you are using a port of Ubuntu Touch being worked on by a community developer. Of course, Android makes full use of the hardware. Would you have brought the Nexus 5 if it was advertised as "working except for bluetooth and some power management issues?"

Not only is Ubuntu for Devices (as it is now called) still being developed but all ports are still an ongoing development process. These are not finished ports. Installing them should still be seen as experimental and an opportunity to join in the development by becoming a tester.

---

### Post by ElToro on 2014-10-27
Although grahammechanical is perfectly right about the state of the build and what to expect, there are a few tricks that might make the SIM work. 

Had the same problem on a Nexus 4, and discovered that switching off the SIM pin and rebooting worked. Made a pin code for the device instead, and adjusted the time to screen-block down to 2 minutes. 

If that doesn't work, you might want to try this:
1) Go to wi-fi settings in system-settings, disconnect from any connected wifi network and turn the wifi off.
2) Turn flightmode on and then off again.
3) Open terminal and type sudo restart lightdm.

---

