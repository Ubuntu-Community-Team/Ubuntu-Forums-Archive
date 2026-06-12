---
title: "dapper xwindows frozen at login screen"
date: 2006-12-07
forum: General Help
---

### Post by ABentSpoon on 2006-12-07
I've been fiddling with 6.06 for several hours now, and have yet to get past the login screen.

When I installed, i was forced to use the "OEM setup" as the live cd would hang with the cursor frozen on a burnt orange screen. Now, as I boot from my hard drive, it will freeze as the login prompt appears.

I've watched the terminal mode as it boots, and there seems to be no pattern where it will hang; anywhere between "starting RAID [somthingorother]" to "testing battery state", so I'm assuming somthing is going on in xwindows itself. I highly suspect the graphics driver, as when it hangs, I finally noticed a very faint shimmer on the console, and durring installation I experienced several (minor) graphics glitches (little blue dots, random short white lines appearing for a second).

I'm running unbuntu 6.06 on gateway.
Celeron processor (approx 1ghz)
integrated graphics card (Intel(r) 82810E Graphics Controller)
and 384 meg of ram (128+256)

I'm finally out of search terms to feed google, so I'm hoping someone here can give me some help.

---

### Post by taurus on 2006-12-07
Boot into recovery mode from GRUB menu and at the prompt, try to reconfigure your X again.  I believe you have to use "i810" as a driver for your graphic card...

```
dpkg-reconfigure xserver-xorg
startx
```
If everything runs fine, then reboot into normal mode with

```
shutdown -r now
```

---

### Post by ABentSpoon on 2006-12-07
Well, I don't think that worked. 

I believe it was already set to the i810 driver (that was what was selected when I told it to autodetect the driver) I then gave it 1684 kB of memory, as it asked if I wanted to allocate any of my system memory to that. I then went through the rest of the screens primarily hitting enter, hoping that what was highlighted represented the values already set. I tried to load xwindows, but it died with error messages that went somthing like this:

> (EE) 181(0): Ring buffer allocation failed
Fatal server error:
AddScreen/ScreenInit failed for driver0

I assumed these had to do with the memory I gave the card, and set it back to blank (i assume it allocates none in that scenario), rebooted, and it crashed as it had been previously.

---

### Post by taurus on 2006-12-08
Instead of using i810, why don't you pick vesa and see if X is running at all!!!

---

### Post by ABentSpoon on 2006-12-08
Well, thanks for the ideas, but nothing seems to be working yet. 

I chose vesa, and entered through the rest of the menus. When I loaded X, a pastel pinstripe screen appeared, reminding me of the curtians in my dad's old room at my grandparents house. I tried booting normally, but nothing appeared after the ubuntu spash screen, where before I at least got to the login prompt.

I forgot to check what the terminal said; I'll go check that out as I wait for replies... no more cold shutdowns for windows... finally  corrupted my system to a point where it would no longer boot.. anyways, thanks for helping me out.

---

### Post by ABentSpoon on 2006-12-08
Alright, I went back in.

With the vesa driver, it hung up at approximately the same spot, but I didn't get any graphics, just a black screen. It had frozen at "Starting Periodic command scheduler", which it had done before,  but had occasionally gotten past.

Hopefully I can get this set up so I can test my server code from home..

---

### Post by K.Mandla on 2006-12-08
Off-the-wall question: Are you using a video card attached to a motherboard with built-in graphics? I've seen some motherboards complicate things by confusing X, because they don't completely disable the onboard graphics and X tries to output to the onboard port.

Just a wacky idea. :roll:

---

### Post by ABentSpoon on 2006-12-08
No.. I'm just using the onboard chip that came with the gateway.

What does it mean when the vesa driver doesn't work? I've heard the vga driver is similar.. i may go check that out..

---

### Post by ABentSpoon on 2006-12-08
I've now tried VGA mode, which didn't do much.

I tried both using the kernel to do some of the graphics, and not letting it. (whatever that means). Selecting NO gave me a fatal error about no screens detected, and selecting YES gave me a very odd noisy page with what looked like refresh rate problems.

Any idea what the basic modes not working means, or what to try next?

---

