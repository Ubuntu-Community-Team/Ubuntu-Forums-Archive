---
title: "Linux unusable after overclocking -&gt; Why?"
date: 2007-01-17
forum: General Help
---

### Post by raul_ on 2007-01-17
I managed to overclock my CPU from 1800MHz to 2150MHz (roughly). Any further and the computer wouldn't boot. So i tried booting Linux, and the booting stalled at 70%, every time. So i  reduced the overclocking to 2090MHz and Linux booted fine. BUT, strange things happened. USP applet wouldn't load (i can't understand why) , HAL failed to initiate, and firefox gave a segmentation faul (core dumped) error. So i had to overclock only 10% of the CPU and that's the factory settings (ASUS K8N seems to have a overclocking option and the max is 10%)

I know overclocking makes computers unstable, but how are these errors related? I really can't understand the HAL and the segmentation fault errors (i won't even mention the USP error...i'll just say "WTF??")

PS: I have read stories of people who could push this CPU to 2400MHz and with crappy/no cooling and other specs

---

### Post by kerry_s on 2007-01-18
There are certain steps you do to overclock a computer, just changing the setting and hopping it works is just asking for trouble. Did you even prep the cpu before you started?

---

### Post by riven0 on 2007-01-18
Yeah, overclocking is dangerous. I don't think you'll be getting that big of a performance gain, but if you still want to do it, you may want to check out [this blog to get some tips]("http://linux-blogger.com/2005/01/11/overclocking-from-processors-to-ram-to-graphics-cards/"). Not sure if it'll help, but it's an interesting read.

---

### Post by raul_ on 2007-01-18
> **kerry_s said:**
> There are certain steps you do to overclock a computer, just changing the setting and hopping it works is just asking for trouble. Did you even prep the cpu before you started?

It depends in what kind of preparation you're talking about. I'm not a hardcore overclocker. I searched for someone who already did the job, saw the limits and went for it. My settings were way lower than the "stable" ones. For example, i found in several websites that i could push the CPU clock ratio to 242 to be stable as rock, and mine was on 230. 

Overclocking is bad if you do it blindly and don't watch your temperature/cpu voltage correctly

---

### Post by Shay Stephens on 2007-01-18
Question: Linux unusable after overclocking, why?

Answer: Overclocking

---

### Post by raul_ on 2007-01-18
> **Shay Stephens said:**
> Question: Linux unusable after overclocking, why?

Answer: Overclocking

Lol. Yeah i got to that part :) i'm just curious about how the system was affected. those errors were ridiculous, and they seem to have nothing to do with overclocking

---

### Post by K.Mandla on 2007-01-18
I believe it's going to differ from chip to chip and system to system. I used to overclock a lot (about five or six years ago, though), and I could have an identical system to a friend, and mine would get 100Mhz more and his would lock up. Or vice-versa.

Probably the standard suggestions apply: If you're serious about OCing, get serious about cooling. Spend the money on proper fans and thermal paste and see what you can get. You might even look into another chip and see if it performs differently. Who knows? :D Fun, though, isn't it?

---

### Post by K.Mandla on 2007-01-18
Oh yeah, I forgot about this:

[http://totl.net/Eunuch/index.html](http://totl.net/Eunuch/index.html)

:D

---

### Post by kerry_s on 2007-01-18
> **raul_ said:**
> It depends in what kind of preparation you're talking about. I'm not a hardcore overclocker. I searched for someone who already did the job, saw the limits and went for it. My settings were way lower than the "stable" ones. For example, i found in several websites that i could push the CPU clock ratio to 242 to be stable as rock, and mine was on 230. 

Overclocking is bad if you do it blindly and don't watch your temperature/cpu voltage correctly

This system that i'm using now is over clocked big time and has been for about three years now. When i over clock i always prep the cpu first, i take everything off it and make sure it's clean then put it back together with all new thermal gel and usually a better fan. When over clocking you want to start slow, not just jump to the highest setting you think it can take. I usually move it up one and run it for a week, this gives the cpu time to burn in to the more power flow and i'll just continue to slowly move it up every week till the system just starts to get unstable then back down 1. That usually is the setting i would use. Be warned though once the cpu has burned in to the over clocked settings, if you try to lower it after that your system will go crazy. I can't even remember what my original clock was, i think it was 1.2, anyways now it 1.6->

     *-cpu
          product: AMD Athlon(tm) XP 2000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 1650MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts

---

### Post by kerry_s on 2007-01-18
Hey, I just checked what my clock was at and there are 7 settings and i was set right in the middle, so i figured what the hell it's been running that for 3+ years that's crank it up a notch. So now i'm up to 1.7 ;) 

     *-cpu
          product: AMD Athlon(tm)
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          version: 6.8.1
          size: 1700MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts

---

### Post by mcduck on 2007-01-18
There is never any guarantee that you CPU could be overclocked to certain speed. If somebody has a same model CPU and can overclock it 20% that doesn't mean you can automatically do the same. That's why you have to test yourself what works with your hardware, instead of just repeating things somebody else has done.

Correctly done overclocking is safe, and doesn't have any real effect on your hardware's lifetime. The hardware gets old and outdated years before overclocking kills it, unless you ar continuously running on the limits with bad cooling and such.

Anyway, the way to do it is to increase the speed a bit, test if it's stable, then increase a bit more, test, bit more, test and so on until it's not stable any more. Then go back a bit and you are fine. 

But remember that being able to boot doesn't mean it's stable, you should run some CPU-intensive program for couple of hours to make sure that it's stable under real stress. Most people use Prime95 to do that (as it's bot CPU-intensive and also able to report if it does any errors), but there is also app called cpuburn in Ubuntu repositories that could probably be used.

---

