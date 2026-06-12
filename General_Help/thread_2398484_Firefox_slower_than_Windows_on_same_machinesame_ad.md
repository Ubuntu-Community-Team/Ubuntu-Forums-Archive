---
title: "Firefox slower than Windows on same machine/same addons"
date: 2018-08-13
forum: General Help
---

### Post by timonoj on 2018-08-13
Hi guys!

I have a laptop with dual boot (Core i5, 8GB RAM, Nvidia 840m and 240GB SSD). I believe the hardware isn't bad at all for normal desktop usage, but in truth, Firefox on Linux lags a lot. I use KDE Neon. Pages take rather long in rendering, and the whole system overall looks underperforming. Where it's definitely most noticeably is on Firefox, although I'm not sure I'd discard it being some CPU issue on linux. I have the official Nvidia drives, but have it running with Prime Indicator Plus under Intel graphics, unless I do gaming. So...it's running on the intel, just like on Windows. But firefox really struggles. Main addons I use constantly: Ublock, Cookie Autodelete, Containers, NoScript. These are the same in Windows, but somehow perform much better there. Battery wise, it doesn't get better mileage than Windows.

What can I look at, to improve the performance?

---

### Post by TheFu on 2018-08-13
I've seen terrible performance with Firefox for about the last 9 months on my main desktop, which runs in a virtual machine.  I've tried about 10 solutions, as recommended on the Mozilla support site. Some helped slightly. 

Sadly, when I run without any addons enabled, performance is fine.  I use some of the same addons you are. So, the first step as outlined at the mozilla site is to run firefox without any addons enabled.  I think they call it safe-mode.

I'd also suggest to you check which GPU and GPU driver is actually being used.  **lshw** will show it.

[https://www.makeuseof.com/tag/5-firefox-runs-slow-browsers-run-fast/](https://www.makeuseof.com/tag/5-firefox-runs-slow-browsers-run-fast/)

On my laptop, firefox performance with a cloned setup (bit-for-bit copy from the desktop), is perfect, fast.

---

### Post by timonoj on 2018-08-13
Thanks! In the end a traditional solution, but seems to still provide insight onto the issue. I still think there might be some additional CPU hindering on Linux, but when running with no add-ons, Firefox became way snappier. So some addon is really taking way too much CPU. I dived onto u-block settings, and disabled the cosmetic filtering, and also the filters, as it's suggested as a way to reduce the CPU on "older" machines. Not that old, a Core i5 with 8BG of RAM...but it really improved performance. So there's that. Still not the perfect solution, as I don't need to do that on Windows on the same laptop.

By the way, lshw does indeed show my drivers are OK. 

Thanks for the help!

---

### Post by TheFu on 2018-08-14
Thanks for posting back what helped.

There are multiple uBlock versions which are made by different organizations. Definitely validate you have the one you intend.

If you consider it solved, please use the "Thread Tools" near the top to mark it that way.  That helps the community.
It is also fine NOT to mark it solved.

---

### Post by timonoj on 2018-08-14
I'm currently using Ublock Origin, which I believe is the most reliable...But yeah, performance is not fully on par with Windows just yet. It's much better, but still not perfect. I'll post here if I ever figure out what it was.

---

