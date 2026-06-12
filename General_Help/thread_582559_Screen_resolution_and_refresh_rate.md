---
title: "Screen resolution and refresh rate"
date: 2007-10-20
forum: General Help
---

### Post by Fred11 on 2007-10-20
I have a Nvidia GeForce 8600GT (256mb GDDR3 RAM) with a 19" Samsung SyncMaster 900SL Plus.

I am using Ubuntu 7.10 (Gutsy Gibbon).
I have installed the proprietary Nvidia graphics card device drivers.

Upon installing Ubuntu, it booted up in 1024x768. It did not auto-detect my monitor. When I click the "Auto" button, it detects wrong refresh-rates. When I choose Samsung SyncMaster 900SL in the monitor thing, I can use 1280x1024 (thats what I want). But the refresh rate is 50 hz. I can only choose 50, 51, 56 hz at 1280x1024, if I select lower resolution, I get more/other options.
After manually changing the Xorg.conf file, I got it up to 60 hz.

I wish to run at 1280x1024 with 100 hz, I am able todo this in Windows XP.

---

### Post by Can+~ on 2007-10-20
100 MHz? That's a bit excessive for an old CRT :shock:. Usually you can work with 60Mhz but this will tire your eyes quick, 70Mhz is the ideal.

---

### Post by Xenix on 2007-10-20
> **Can+~ said:**
> 100 MHz? That's a bit excessive for an old CRT :shock:. Usually you can work with 60Mhz but this will tire your eyes quick, 70Mhz is the ideal.

Not really excessive at all. My Sony 17" Trinitron CRT can do 100Hz in Windows. But it can't in Linux.

---

### Post by mahiyar on 2007-10-20
There is some confusion between interlaced refresh rates and plain refresh rates. Whatever the refresh rates if there is no flickering it should be OK. If you have Nvidia card/drivers installed go to CLI  >>sudo nvidia-settings (do a tab to get the correct selection, as Iam not sure). From the Nvidia settings box you will get all the options, after selecting and trying it out click the option which "writes to your X-org files". I guess that should do.

---

