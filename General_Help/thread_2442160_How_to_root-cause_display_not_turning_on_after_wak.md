---
title: "How to root-cause display not turning on after wake? - new kernel solves problem"
date: 2020-04-30
forum: General Help
---

### Post by bingbong6 on 2020-04-30
Edit: disregard. New kernel did not solve the problem 


I'm using kubuntu 20.04 but I also tried manjaro xfce 20.0 and Ubuntu mate 20.04. All used kernel 5.4 via live boot, all had the same problem:

When waking from resume my Lenovo e585 with ryzen 7, Vega 10 gpu, and an nvme drive, would 50% of the time not turn on the monitor. Alt+ctrl+F2 or Alt+ctrl+F1 does nothing. Connecting to an external monitor however, it turns on everytime.

Switching to kernel 5.6 via ukuu in kubuntu solved this issue. 

But I'd like to understand what the root cause was. I'm guessing it's some power management change, change to the way it sleeps, or a change to the driver for the nvme disk? 

What logs can I generate while running 5.4, that would show drivers used or power management protocols used, so I can do the same in 5.6 and compare? There is the github comparison [https://github.com/torvalds/linux/compare/v5.4...v5.6](https://github.com/torvalds/linux/compare/v5.4...v5.6) but that is extremely tedious and I can't code so I'm not sure what I'm looking at when I read it.

---

