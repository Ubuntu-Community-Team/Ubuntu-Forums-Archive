---
title: "booting with cpu limit command"
date: 2006-11-28
forum: General Help
---

### Post by leetrefz on 2006-11-28
slush1000 gave me this life-saving advice for turning down my cpu:
> 
install cpufrequtils through adept and with every reboot I open a root console and enter both:

cpufreq-set -c 1 -u 2400000
cpufreq-set -u 2400000

The second command works for me and I'd like to not have to enter it every time.

What's the way to have 'er boot with this command?

---

