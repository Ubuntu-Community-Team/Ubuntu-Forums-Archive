---
title: "Cpu Usage"
date: 2008-05-14
forum: General Help
---

### Post by anotherdisciple on 2008-05-14
I'm a bit confused... when I'm not using my computer... it is just on... the cpu will alternate between cores using about 50% of one and 0% of the other... then it will use 0% and 50%....etc. At the time that it is doing this I am not running any programs except the system monitor that I'm getting this info from. In the processes I can sort by cpu usage and it will be 0 for everything except the system monitor... and that is only 2.... so why am I using 25% of my overall cpu when nothing is running?

---

### Post by ibuclaw on 2008-05-14
Firstly, there is Gnome.
Gnome takes up quite a bit of Processing Power to keep is running.

Secondly, there is Compiz (if you have a GL-enabled Graphics Card).
Wow! Wobbly Windows, Water Ripples, Painting Fire, A Desktop Cube, A Rendered FishTank that goes inside that cube (if you have the latest git version). Snow, The Window Decorator...

Thirdly, Open up "System>Administration>Services" and have a look at what's running (half of which you probably never use!)
(...Tracker, Bluetooth Manager, Evolution Alarm Notifier, Visual Assistance...)

Fourthly, How much swap do you have? How much of it is being taken up?

It all adds up.

If you want to save more CPU power.

A) Open up "System>Preferences>Power Management"
And change your "Computer speed policy" to "**Based on processor load**".

B) Press Alt+F2, type in "gconf-editor"
Go into "/apps/gnome-power-manager/cpufreq" in the registry.

Then change the "performance_ac" and "performance_battery" to a value that seems reasonable (100 = Full CPU power, 0 = PowerSave where applicable).

I like to keep mine at even-stevens 50.
But remember! This doesn't slow down the speed of your system.
Afterall, when a heavy app loads, the CPU will always give it's full power to making sure it runs as efficiently as possible.

But at times when you are doing nothing, it will keep things to an absolute minimal.

Hope this gives you some helpful inside knowledge.

Regards
Iain

---

