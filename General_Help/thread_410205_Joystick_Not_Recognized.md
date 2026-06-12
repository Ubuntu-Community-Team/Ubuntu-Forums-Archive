---
title: "Joystick Not Recognized"
date: 2007-04-15
forum: General Help
---

### Post by Virgo53 on 2007-04-15
Hello all,
I could use some help in getting my joystick recognized- it's a Nintendo 3D (model NJS-3D1) for PCs. It has a 15-pin (DB-15) connector for a game port. I bought a Belkin USB Joystick adapter to connect it via USB, but so far can't get Ubuntu to recognize it's plugged in. My sound card is a Creative Sound Blaster Audigy 2 ZS.
I've read and tried the HowTo: Joystick/Gamepads Under Ubuntu posted by adamo509 and HowTo: Enabling An Analog Joystick (+Flightgear) posted by evilghost. I've installed both Joystick and Joystick Calibrator but neither have detected the joystick. The results of running cat /dev/input/js0 through js3 are
"No Such Device." The manual's supported controllers are a CH Flightstick Pro or a ThrustMaster. Any help will certainly be appreciated!  :confused:

---

### Post by ArchStanton on 2007-04-19
I started to try and set up a controller through the gameport, and found myself getting frustrated as well. THen I just put in a usb gamepad and it worked fine. For the price of a cheap gamepad, it wasn;t worth me stressing. If its a nicer joystick, well, thats a different story.

---

### Post by Virgo53 on 2007-04-19
Yes, I know it's an old joystick- I bought it in 1998,  but it's hasn't been used much and is still almost like new. The problem is with the Belkin USB adapter-

It's only for a Microsoft Sidewinder, so I've placed it on eBay and ordered an adapter that will work properly- an RM-203 Rockfire USB Gameport Converter USB Joystick Adapter.

I'd like to credit Vojtech Pavlik (Director SuSE Labs) <vojtech@suse.cz> for his generous help in determining the correct USB adapter. Will post results on it later- stay tuned!

---

### Post by Lupine on 2007-07-20
So, what are the results?  Was thinking about purchasing/testing one of these on an old steering wheel controller I have.  It's only $24 on coolgear.com.

Any feedback?

---

### Post by fdrake on 2007-07-20
can you post here your outputs:
sudo lsusb -v

---

