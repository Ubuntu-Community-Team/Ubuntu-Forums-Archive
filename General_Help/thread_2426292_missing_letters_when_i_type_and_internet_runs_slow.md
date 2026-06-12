---
title: "missing letters when i type and internet runs slow"
date: 2019-09-06
forum: General Help
---

### Post by seetheclay2 on 2019-09-06
my PC will randomly start missing characters and repeating characters at random. at the very same instant, the internet speed on this PC only will tank. i.e. ping goes from 30ms to 110ms, DL speed goes from 250mbps to 15mbps. every other PC's internet is unaffected, it only happens on this PC. once this begins neither issue will go away until i reboot. sometimes if i unplug the keyboard and plug it in to another port the keyboard will type like normal but the internet speed is still slow.

some facts:
[LIST]
[*]currently running elementary OS juno. previously was running POPOS. hardware hasn't changed and the issue happened on popOS the same as it happens now on elementary.
[*]this PC dual boots to windows 10 which has not one single time in the many years i have had it shown these behaviors.
[*]kernel 5.2.11. upgraded from 4.5.xxx last week to see if that alleviated the issue. it did not.
[*]multiple keyboards tested: cooler master quickfire, tecware phantom, custom boardwalk compiled with QMK (no qmk related files have been installed or copied to elementary OS)
[*]htop shows nothing of consequence going on at the time this happens, CPU cores run at 10% or below. RAM usage is no higher than 4GB. etc...
[/LIST]

example of the output from my keyboard when i'm having this issue:
```
[COLOR=#747F8D][FONT=inherit]does anyone know why my keyyyyyyboard evenally does **** like that <-- and often tmes just misses chartersthati type ? [/FONT][/COLOR][COLOR=#747F8D][FONT=inherit]it worksfinefor a randm amoun of tim eand thne i haveto resart o fx it[/FONT][/COLOR]
```

can anyone tell me what is going on? googling this has yielded results like checking the repeat keys is turned off in linux, tried that it didn't work. someone suggested that the mouse refresh rate should be set to 40ms but that was further indicated to no longer fix the issue beyond a specific kernel release. i cannot find a post where someone has anything similar to a simultaneous issue with the keyboard and internet at the exact same time. i'm keen to do some digging into my system i just don't know where to start.

thanks!

---

### Post by Autodave on 2019-09-06
2 things come to mind:

1. Try another keyboard.  Keyboards die and do many funny things.
2.  How many USB devices are you running?  If more than the keyboard and mouse, try disconnecting all of them and see what happens.  Possible that you have a weak power supply or some USB device is pulling the 5V line too low.

Let us know what you find and also please tell us the specs on your equipment.

---

### Post by seetheclay2 on 2019-09-06
Hi autodave, thanks! i have tried multiple keyboards. the only USB device i'm using other than my mouse/keyb is my headset, a cooler master mh752. the keyboard issues have not recurred tonight but i will try removing the headset next time it happens to see if it fixes it.

specs (custom build):
i7 2600k
12gb ddr3 ram
450 watt power supply
2 256GB SSD, 1 1TB spinning drive
radeon r7 200

---

### Post by sdsurfer on 2019-09-09
Usually when I experience this something intensive is running in the background, in my case I can't do nearly anything if clamav is doing a scan. ps -aux in a terminal to see what's running and using resources?

---

### Post by haplorrhine on 2019-09-09
In my minimal experience, I vaguely remember the omission of ASCII characters that seemed to be related to the browser or some connected application.  If I knew more, I might have more tightly sandboxed possible applications.

---

### Post by oldfred on 2019-09-09
Sticky keys can also be an issue.
Dirt/crud/crumbs under keys or just worn out key.

---

