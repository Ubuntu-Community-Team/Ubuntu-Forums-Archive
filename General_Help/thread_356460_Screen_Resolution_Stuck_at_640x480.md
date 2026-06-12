---
title: "Screen Resolution Stuck at 640x480"
date: 2007-02-08
forum: General Help
---

### Post by Bill Bickley on 2007-02-08
I'm a total newbie just getting started with 6.06 LTS.  Everything was going astonishingly well until I did an update.  When I rebooted the machine, the resolution had gone from 1280x1024 to 640x480.

The screen resolution preferences box doesn't show any option other than 640x480.  What did I break?

TIA.

Bill

---

### Post by Surgeon General on 2007-02-08
hi, you can do one of two things:

1. from a terminal windows, do a "sudo dpkg-reconfigure xserver-xorg" then restart X afterwards by pressing Ctrl+Alt+Backspace keys.

2. i'm assuming you're using a laptop (you didn't mention your system config) you can install the 915resolution package (on an Intel video chip) or another package meant for ATI (just search the forums I forgot the name).

hth.

---

### Post by houstonbofh on 2007-02-08
> **Bill Bickley said:**
> I'm a total newbie just getting started with 6.06 LTS.  Everything was going astonishingly well until I did an update.  When I rebooted the machine, the resolution had gone from 1280x1024 to 640x480.

The screen resolution preferences box doesn't show any option other than 640x480.  What did I break?
You broke your video driver. :) It failed and fell back to 640x480.  First, what is your video card?  Second, did you do anything in Dapper to better use that video card?

---

### Post by Bill Bickley on 2007-02-08
Thanks so much.  Back in business!

Bill

---

