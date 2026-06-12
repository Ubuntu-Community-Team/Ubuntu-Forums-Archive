---
title: "Fix for getting mic and headphones to both work on the MacBook (and pro?)"
date: 2006-11-13
forum: General Help
---

### Post by jasonparekh on 2006-11-13
Hey all,

I spent some time to try to get a solution for both the microphone and the headphone jack to work (so it properly mutes the internal speakers when headphones are plugged in).  I'll just quote my blog: (I would post the full article here, but it's a bit long)

> The current (2006/11/12) state of ALSA for the MacBook (and MBP, ..?) is pretty strange: If you&#8217;re using a vanilla kernel, chances are your headphone sensing works (when you plug in headphones, your internal laptop speakers mute and you hear audio from your headphones). If you&#8217;re using a mactel-patched kernel (or the generic Ubuntu kernel, maybe other distros that prepatch with mactel), chances are your microphone has the ability to work (you have to toggle between Line-in and Mic on the ALSA mixer for it to work), but your headphone sensing doesn&#8217;t (when you plug in headphones, you hear audio from both the internal speakers and the headphones).

You can see the solution (need to rebuild the kernel) on my [Linux on MacBook]("http://www.jasonparekh.com/linux-on-macbook/#microphone") section.

jason
[blog]("href="http://www.jasonparekh.com")

---

