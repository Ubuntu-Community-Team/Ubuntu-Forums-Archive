---
title: "Random reboots, kernel panics, memtest errors, help!"
date: 2013-12-24
forum: General Help
---

### Post by john_ladasky on 2013-12-24
Hi folks,

I had a nice, stable Ubuntu 13.04 system running for months.  Of course, I had to go and mess with it.  Now I'm getting a lot of trouble.  Is it my fault?  I don't know.  The errors didn't start right after my changes, they appeared a few days later.

Here's my configuration:

Motherboard: Gigabyte MA78GM-US2H, vintage 2009.
CPU: AMD Phenom II x6 1100T.
RAM: four 2 GB G.Skill DDR2 1066 MHz SDRAM sticks.
Operating system: upgraded December 13, from Ubuntu 13.04 x64 to 13.10 x64.  Single-boot system -- no Windows.
GPU: upgraded December 17, from an NVidia 460 GTX to an NVidia 760 GTX; running an NVidia proprietary driver, from the 319.XX series as recommended by Ubuntu.

I'm generally good about installing hardware.  I have an anti-static wrist strap, and I make sure I'm grounded while working with components.  In any case, my problems did not start right away, so I can't reliably attribute them to the new hardware.  
 
When trouble starts, what I see at first is one of two things:

1) My desktop pointer may begin to lag, and ultimately freeze.  I was hoping to get the System Monitor open, but the system is too sluggish.  Ultimately I push the reset button and reboot.
2) The system may simply crash and reboot itself without warning.

Upon rebooting, I get the GRUB menu.  I don't normally get the GRUB menu, since my system only has Ubuntu on it.  After selecting the default choice, one of four things can happen:

1) I might get back to the Unity login screen -- and, for a while, all is again well.  It might be hours until my next crash.
2) I receive a message like the following after the GRUB menu: "Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)", at which point the system appears to freeze.  After waiting about 30 seconds or so, I push the reset button.
3) The system black-screens right after the GRUB menu, and reboots itself.
4) Right after the PCI devices listing (the page that appears after the BIOS page), I get the message "Begin to update backup BIOS to latest version...", and then the system reboots before even reaching the GRUB menu.

On my latest boot attempt, I decided to try a memory test from the GRUB menu.  Memtest86 is reporting MASSIVE numbers of memory errors. I have a million errors and counting! After running for about 90 minutes, my office was noticeably warm (from running Memtest?). I shut the system down.

I generally don't play with my BIOS.  I don't overclock, or adjust voltages.  Other than configuring the timings for my RAM (years ago), and doing a flash BIOS upgrade to allow my system to use the six-core CPU, I have left it alone.

I know that the GPU interacts with the system very deeply.  Could the GPU upgrade be the cause of my problems?  I might restore the old video card to the system as a test -- but I also upgraded the video driver when I upgraded the OS, so it wouldn't really be going back to the original configuration.  I recall that, when using Ubuntu 13.04, my NVidia driver was from the 310.xx series.

I know that [_I had similar problems_]("http://ubuntuforums.org/archive/index.php/t-1960714.html") 18 months ago, when I upgraded the GPU card from a GTS 8800 to the GTX 460.  At the time, NVidia happened to have accidentally forked its drivers, giving people with both old and new GPU cards headaches simultaneously.  I had Unity desktop lags and freezes, somewhat like I'm seeing now.  However, my problems would start within a few seconds of logging in.  It didn't take hours for the system to crash, like it is doing now.  Also, back then, I didn't see any kernel panics, nor did I run a memtest.

As a final note, I should mention that I've read a few posts here on Ubuntu Forums in which users report problems with the NVidia 319.xx driver series.  I'm looking through those posts to see whether their symptoms might match with what I'm seeing.

Any advice you might have is greatly appreciated!

---

### Post by john_ladasky on 2013-12-24
Followup: this morning I rebooted.  Aside from seeing the GRUB menu, everything is normal now.  I hope someone who reads this today might be able to offer me some insights.

I just installed PSensor to monitor system temperatures.  I used it once on an earlier Ubuntu installation.  Compared to earlier versions, PSensor appears to be a bit broken.  I can get it to hang just by trying to make adjustments to the settings, does anyone else have that experience?  Anyway, I'm looking to see whether system loads and/or heat are correlated with crashes in any way.  So far, I'm looking at a CPU in the 30 - 33 C range, a GPU in the 39 - 41 C range.  Nice and cool.  I'm conscientious about fans and heat sinks.  I would also like to monitor RAM temperature if that is possible with my motherboard -- however, as I mentioned, Psensor hangs on me if I open any menus.

---

### Post by john_ladasky on 2013-12-24
Followup the Second: I just ran one of my more demanding applications for 30 minutes, and simultaneously, I did a lot of web browsing.  CPU loads climbed to about 75%.  Both my CPU and GPU temperatures rose into the 53 - 59 C range, warm but still well within acceptable limits, I think.

When my demanding application stopped running, CPU temperatures returned to the low 40's within two minutes.  The GPU temperature lagged a bit, but also started to drop.  It reached a plateau at about 50 C.

I was a little surprised to see the GPU temperature climb as much as it did, when I know that my application should not be using it.  My app is a program I have written myself in Python.  It makes use of multiprocessing, and runs on all six cores of my CPU.  But it doesn't display any graphics worth mentioning, nor does it use CUDA (yet).  I would like to see whether the GPU is, in fact, being used -- by Unity, perhaps? -- but as I mentioned, PSensor is not cooperating with me.

Still hoping for some insight.  Thanks!

---

