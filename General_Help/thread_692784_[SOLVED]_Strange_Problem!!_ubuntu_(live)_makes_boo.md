---
title: "[SOLVED] Strange Problem!! ubuntu (live) makes boot memory test slow (1min!)"
date: 2008-02-10
forum: General Help
---

### Post by Arutha on 2008-02-10
[COLOR="Red"]Short description of problem:

I started a ubuntu gutsy live session on my overclocked WinXP computer. I installed a video codec and tried to install nVidia graphics drivers, upon which i was asked to reboot. the reboot failed and since then the boot memory test takes welll more than 1 minute to complete (before: 1 second). I removed the ubuntu disc, of course.[/COLOR]


[COLOR="Blue"]Detailed description of problem:

After the failed reboot, I thought that I couldn't boot at all, because the system seemed to hang at the word "memor" (yes, without "y"). I panicked, but then I realized, that it simply takes more than 1 minute for the memory test to complete. Also, all BIOS overclock settings were reset to default values. I can boot windows, but there is another hang-up for about 40 seconds during the windows startup (when the desktop is already displayed and all tray icons are loaded, too - system seems totally frozen at this time).
Another thing: the BIOS is ignoring my clock settings, but not my voltage settings. I changed all settings back to my original overclock, but when I start windows, the clock speed is at default. Then, when I reboot again and check the BIOS, the settings are still the ones which I entered!
At some point, I even cleared my CMOS with the jumper on the mainboard, that didnt help, too. I also disconnected the power cord for a few minutes and pressed and held the power button on the case for 10 seconds, but it didnt help[/COLOR]

[COLOR="SeaGreen"]My system at default speed:
Gigabyte DS3 revision 3.3, firmware F10
200 Mhz Front Side Bus
E4300 Core 2 Duo, 1.8 Ghz, 1.325v
Corsair XMS2 DDR2 memory 800Mhz (Dual Channel), divider 4:3, 1.8v, 5-5-5-15

My original (overclocked) system:
333Mhz Front Side Bus
  CPU running at 3.0 Ghz
  Memory at 888Mhz, divider 4:3, 5-5-5-15
CPU voltage 1.375 (+0.050)
DDR voltage 2.0 (+0.2)[/COLOR]

[COLOR="Red"]It's freaking me out that the problem which apparently was initiated by a live session of an ubuntu CD, which is now completely removed from the computer (and microwaved, btw -.- ), still persists!! i know that linux can interact more directly with hardware than windows, but I'm at a total loss here?!?! 
How is this possible, help please !!![/COLOR]

---

### Post by Arutha on 2008-02-11
Ok Problem solved !!!

I think I know what was the problem --> my stupidity :D

My Bios can save configurations (outside the CMOS, not affected by clear CMOS jumper), and I loaded my original overclocked config. But as a safety measure, it seems that the BIOS always sets "manual clock control" to DISABLED. I didnt see that. So of course I couldnt overclock my PC...

Once I changed it to ENABLED, the memory boot up testing was ok again, too. I think the memory boot up testing was slow because my RAMs were PC6400, but running at only 533 Mhz.


Oh and I didnt really microwave the Ubuntu CD. I just said that because I was angry *g

I still won't try ubuntu again on my fast machine, but I have an old AthlonXP where I'm very looking forward to installing and trying ubuntu!!

---

