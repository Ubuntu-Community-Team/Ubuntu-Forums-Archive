---
title: "Hard drive busy light always on"
date: 2007-03-29
forum: General Help
---

### Post by Ubunthree on 2007-03-29
I am dual-booting on a sort-of-old HP Pavilion 8670C, with Windows 98 on its original 30 gig hard drive. My Ubuntu system lives on a second 100 gig hard drive which I installed without any apparent problems. One thing which I notice when I run Ubuntu is that the hard drive busy light is on at all times, whatever I am doing, no matter how long the computer has been on, and even after the shutdown routine completes and the machine is waiting to be turned off. The drives are both IDE type, and my master/slave jumpers are correct as far as I know. My questions:

- Is the light actually indicating disk activity, or is it just confused by the second drive's presence? Do I need to change something to get it to turn on/off correctly?

- Is one or both of the drives doing something which it doesn't need to be doing, which would cause less wear on it/them if it were stopped?

- Can I tell which drive's status the light is indicating?

- Does Ubuntu have a setting to turn off the drive motor, as Windows does, during idle periods?

Thanks for any answers!

---

### Post by kellemes on 2007-03-31
It seems likely it's a led-cable issue.. Is it connected the right way? Maybe you should simply unplug the cable all together.. personally I hate lights telling me the disk is working, my hearing is fine..

Find your motherboard-specs/diagram to find out where to connect the cable to get the signal from the correct HD, but maybe the board is ´confused' as you say ;-)
You can use 'top' to see if some major activity is going on, but I don't think it will be..
About shutting down the drive.. I don't know actually..

---

### Post by Ubunthree on 2007-04-01
I don't have any specs or diagrams for this thing. The two LED cable plugs - one for power, one for drive - go onto pins labeled PLED and IDELED on the board. Adjacent to these are pins for the power switch itself, and for a reset button, which the machine didn't come with, but which I added myself long ago as a necessity for running Windows, heh... I don't see any other connections for LEDs. Ah well, I don't think it's anything important; it's just the sort of thing that always makes we want to know what's going on. Thanks for the response.

---

