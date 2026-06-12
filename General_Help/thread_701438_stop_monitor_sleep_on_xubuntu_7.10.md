---
title: "stop monitor sleep on xubuntu 7.10"
date: 2008-02-19
forum: General Help
---

### Post by Toky on 2008-02-19
This request might seem odd, but I need to keep my xubuntu desktop visible at all times but the screen keeps going blank after 20mins.

I've read a couple of the posts that i'va found about this topic but they have not helped.

for completeness:
Monitor DOES NOT have anyway of putting it self to sleep (at least none of the ones we have here)
Bios does not have any option for monitor/video card sleep/shutoff

screensaver bar does not have a way to put it on never, the lowest it'll go is 1 minute and the longest is 2hrs.
I've disabled acpi on the system.

I have about 1 week to fix this, since the boxes will be deployed in 1 week.

Thanks

---

### Post by Peter6218 on 2008-02-19
> **Toky said:**
> This request might seem odd, but I need to keep my xubuntu desktop visible at all times but the screen keeps going blank after 20mins.

I've read a couple of the posts that i'va found about this topic but they have not helped.

for completeness:
Monitor DOES NOT have anyway of putting it self to sleep (at least none of the ones we have here)
Bios does not have any option for monitor/video card sleep/shutoff

screensaver bar does not have a way to put it on never, the lowest it'll go is 1 minute and the longest is 2hrs.
I've disabled acpi on the system.

I have about 1 week to fix this, since the boxes will be deployed in 1 week.

Thanks

It's in Power Management. Set it to Never. Doesn't work on all comps however.

---

### Post by Toky on 2008-02-20
There has got to be a way to keep the OS from sending the sleep command to the video card.

---

### Post by Rmantingh on 2008-03-10
I had a similar problem. Apparently you need to install "gnome-power-manager".
Once installed a button will appear in the screensaver settings screen called "Power Management".
From there you can set the sleep timeout to "Never".

---

