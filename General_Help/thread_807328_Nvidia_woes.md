---
title: "Nvidia woes"
date: 2008-05-25
forum: General Help
---

### Post by Chris Murphy on 2008-05-25
I just upgraded to 8.04.  Install when great, worked no problem for the first little while.  Problems started when I tried fixing the blurry font issue, which I eventually sorted out.  This brought up another problem, the resolution being stuck at 640x480 at 50hz, since i have a relatively new(8500gt) video card and a 17" lcd, this isn't exactly acceptable.  I've read up on that problem and none of the proposed fix's worked, nvidia-settings doesn't give me any other choices, and when i try recongfiguring xorg, it asks me about my keyboard a bunch, but doesn't let me change ANY video settings.  After trying several proposed fixes I was unable to log into anything but terminal and have gotten error messages such as these:

kinit: trying to resume from /dev/disk/by-uuid/e1c767fo-1484-427e-831d-31adf282c7ed
kinit: no resume image doing normal boot...

b43-phy0 ERROR:  You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and dowload the correct firmware (version 4).
b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found or load fail.

At this point I reinstalled Kubuntu fresh, started installing packages again, and now am getting the same error again after a couple successful boots.

My current theory is that the wireless errors are unrelated to my being unable to reach KDE, as that wouldn't make sense, and I'm actually have problems with X, or the nvidia drivers(which have always caused me problems in the past).

I'm at a loss as to what to do next.

---

### Post by Chris Murphy on 2008-05-25
The possibility that i'm have an unrelated hardware issue causing the no boot such as a bad hard drive(i think i got a similar no resume image error before with a bad hd, but I can't remember), has also occured to me, although I'm unsure how to confirm.

---

### Post by Chris Murphy on 2008-05-25
bump

---

