---
title: "Just wondering ... :/"
date: 2006-11-08
forum: General Help
---

### Post by zgornel on 2006-11-08
I compiled today the lastest vanilla kernel from kernel.org :2.6.18.2 (2.6.17 kernel sources from repositories won't even compile ... hello ubuntu staff ??). Some "curious facts i noticed" : 
1. 150 mb more free memory (i have 512).
2. Slow graphical performance - mouse cursor was choppy, gnome session wouldn't even load after 5 minutes of blank, brown backgroud (direct rendering on, i915 and drm modules loaded and working). 

The modifications I made to the kernel were to select the processor type (Pentium M) instead on 586, disable SMP and kernel debugging, which leads me to the first question: why is kernel debugging enabled ? Ubuntu is very user oriented so I see no reason whatsoever for the kernel debugging option to be enabled. 
Second question, why is there so little ... I don't know how to call it ... let's say incompatibility between the vanilla kernel and the distribution itself ? 
In my opinion, being able to compile the kernel is one of the most important aspects of linux (linux = the kernel), the rest is just bloat from a certain point of view. I feel a bit frustrated, hope I'm not misunderstood, I really like ubuntu but after several years of slackware I have the feeling that the eye candy and windows-like usability effort could have been used in other areas.

P.S Maybe I should have posted this to the Cafe section ... :-?

---

### Post by bsussman on 2006-11-08
> **zgornel said:**
> 
In my opinion, being able to compile the kernel is one of the most important aspects of linux 

P.S Maybe I should have posted this to the Cafe section ... :-?

Yes - I do think it belongs in Cafe - ubuntu seems to be aimed at the  non-technical MS mainstream user.

The ones who will probably never compile anything, let alone a kernel.

No ubuntu staff time has been spent on the dev environment - it is a box-stock debian type environment.  So it ain't harder, but it ain't easier.

---

### Post by PriceChild on 2006-11-08
Could i ask whether you imported the settings from a previous "official" kernel... or just thought that the standards given on this new compile were the default for all ubuntu kernels?

---

### Post by zgornel on 2006-11-08
> **PriceChild said:**
> Could i ask whether you imported the settings from a previous "official" kernel... or just thought that the standards given on this new compile were the default for all ubuntu kernels?
I imported the settings from the standard generic edgy kernel and manually removed the stuff i did not need ( i'm compiling kernels since 2.0 version so i'm not new at his).

---

### Post by PriceChild on 2006-11-08
> **zgornel said:**
> I imported the settings from the standard generic edgy kernel and manually removed the stuff i did not need ( i'm compiling kernels since 2.0 version so i'm not new at his).Sorry I didn't mean to cause offence... it just doesn't hurt to check the simplest things :)

---

### Post by zgornel on 2006-11-08
Totally agree. Not offended. Just frustrated ...

---

### Post by zgornel on 2006-11-09
Kernel compile problem solved (it seems my X behaved strangely if I disables SMP support in the kernel).
Solved also a problem that I had and saw others had (it was reported on the forum when Edgy was in testing): compiling the kernel source (2.6.17-13 from the repos) gave a *undifined reference to touch_nmi_watchdog()* and exited. I looked up the ide_wait_not_busy() function and it's reference to touch_nmi_watchdog(). I found it in linux_source/drivers/ide/ide-iops.c (at the end of the file). I commented the call of the function so it looked like this:[I]
#ifdef CONFIG_X86
                //touch_nmi_watchdog();
#endif[/I]
This shouldn't be of significant importance, the official 2.6.17 kernel does not even include this section of code. 
Give some feeback if this did get the job done for you or some advice about resolving the problem without commenting the line (including a .h).

---

