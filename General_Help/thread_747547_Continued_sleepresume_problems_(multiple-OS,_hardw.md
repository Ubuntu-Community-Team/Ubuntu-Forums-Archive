---
title: "Continued sleep/resume problems (multiple-OS, hardware related?)"
date: 2008-04-06
forum: General Help
---

### Post by twin_57103 on 2008-04-06
I've got a new home-built computer that I love, except for continued sleep/resume issues.  It's dual-boot Ubuntu 8.04 (beta) and Windows Vista (SP1).  I had to use Hardy because something in the hardware simply isn't supported on earlier versions of Ubuntu.  I've installed the NVIDIA proprietary drivers for Ubuntu, and checked that the Windows video, keyboard, and mouse drivers are up-to-date.

Here is my problem: I'll allow the computer to go to sleep, then when I press the space bar to resume (it's set to use space bar from the BIOS), the fans come on and the power light goes solid, but nothing else resumes - keyboard is unresponsive, including num lock.  The keyboard is PS2, mouse is wireless USB (but not set to wake from mouse).

Because this occurs in both Linux and Windows, I suspect it is not OS-related.  I've been troubleshooting from a hardware- and BIOS- perspective.  I've updated the BIOS.  I'm now playing with sleep settings from the BIOS.  It was set to S1&S3, and I've just changed it to S3 alone.  Any other suggestions?  I'd be happy to post photos if that's helpful.

Motherboard: ASUS M2N-SLI Deluxe
Processor: AMD Phenom 9500 quad-core (2.2 GHz)
Memory: 4 Gb PC6400, 2 x 2 Mb (Super-Talent)
Video Card: EVGA e-GeForce 9600 GT
Hard Drives: 2x Hitachi SATA II 320 Gb
Optical Drives: 2xLite-On 20X DVD-RW
Power Supply: 700W Coolmax Green Power
Operating Systems: Ubuntu 8.04 beta and Windows Vista SP1

---

### Post by twin_57103 on 2008-04-07
Solved, I think...I disabled S3 sleep in favor of S1.  The standby energy usage will be slightly higher, but so far, the computer has resumed properly.

---

### Post by twin_57103 on 2008-04-08
It looks like that solved the system error, but Ubuntu isn't very happy about resuming (Windows works perfectly now).  I left it last night to sleep on its own and when I got up this morning, the power was fully off and I got a bubble notification that said that suspend had failed (kicking myself for not taking a screen shot).  I also accidentally clicked the "do not show this message again" (my mouse is a little spastic) - oops!

Can anyone help me troubleshoot this?

---

