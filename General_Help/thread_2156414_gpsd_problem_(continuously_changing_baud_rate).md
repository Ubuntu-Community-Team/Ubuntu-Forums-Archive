---
title: "gpsd problem (continuously changing baud rate)"
date: 2013-06-21
forum: General Help
---

### Post by philipp625 on 2013-06-21
Hi,

I have a Trimble ProXT GPS receiver which I connect to a laptop using a serial-to-USB converter. I use gpsd to access the GPS data. This works very well on my old laptop with Kubuntu 10.04 and gpsd 2.92, but I cannot make it work on my new machine with Kubuntu 12.04 and gpsd 3.4.

I ran the command "gpsd -n -N -D4 /dev/ttyUSB0" on both machines, and that's what happens:
[LIST]
[*]10.04/2.92: gpsd tries out different baud rates, until it has found the correct one (38400), then I start getting GPS packets. 
[*]12.04/3.4: first, it starts similarly, gpsd detects the baud rate and starts displaying the GPS packets. But after a few packets, it starts iterating through the baud rates again, starting with 4800. Then another 3-4 packets are displayed once it reached 38400, and then it starts searching with baud rate 4800 again, and so on... 
[/LIST]

I tried to fix the baud rate on the port of the GPS device manually, I killed gpsd, typed "stty speed 38400 </dev/ttyUSB0" and then started gpsd. That didn't change anything. Anyway, I don't see why this should be necessary all of a sudden.

Is there anyone who experienced a similar problem? Any help would be greatly appreciated.

---

