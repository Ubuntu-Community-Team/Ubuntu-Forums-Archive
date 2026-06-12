---
title: "radeon driver and x1300 video card, youtube jerky and slow"
date: 2014-02-08
forum: General Help
---

### Post by sdowney717 on 2014-02-08
Is it not hardware accelerated? Or what?
Not smooth, not pleasant to view, not something you want to watch.

What is you experience with x series video cards and the radeon driver?

---

### Post by Bashing-om on 2014-02-08
sdowney717; Hi !

I run:
> 
sysop@1310mini:~$ lspci -nnk | grep -iA3 vga
06:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146]
        Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2342]
        Kernel driver in use: radeon
06:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]
sysop@1310mini:~$ 

And my experience is most excellent. I have no issues; 3D acceleration is good.
- AMD platform on an old obsolete Abit KN9 motherboard, Award Phoenix BIOS -

[INDENT][INDENT]if it ain't broke
[INDENT][INDENT][INDENT]do not fix it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Stormlord on 2014-02-08
To my knowledge, hardware acceleration is not supported on Linux by Adobe flash.  So, no matter what flash you are using, normal or pepper flash (embedded in Chrome), software rendering is the only option.  Flash games go slow too unfortunately because of this.  :/

---

### Post by sdowney717 on 2014-02-08
Computer is using 13.10
Now it is an AGP card and a 2.8ghz pentium CPU.

Are your systems using PCIE?

If I watch a youtube, what I get is stopping and starting of the video, so its like massive frame loss type experience.
It did this in small window or large window.

It is a dual boot with windows 7, and it plays much better in win7 which makes me think the hardware is ok.

---

### Post by sdowney717 on 2014-02-08
> **Stormlord said:**
> To my knowledge, hardware acceleration is not supported on Linux by Adobe flash.  So, no matter what flash you are using, normal or pepper flash (embedded in Chrome), software rendering is the only option.  Flash games go slow too unfortunately because of this.  :/

Could be the single core 2.8ghz intel cpu then?

---

### Post by Mark Phelps on 2014-02-08
> What is you experience with x series video cards and the radeon driver? 

When using the default Radeon driver, and an x1650, I had no problems.

Realize, however, that AMD dropped restricted driver support for the X-series years ago -- so today, you're stuck with the default Radeon driver.

---

