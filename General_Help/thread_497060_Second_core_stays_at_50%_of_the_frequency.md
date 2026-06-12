---
title: "Second core stays at 50% of the frequency"
date: 2007-07-09
forum: General Help
---

### Post by panicb on 2007-07-09
I have Athlon X2 dual core cpu, and I have CPU frequency monitor on the gnome panel.
Normally, both cores stay at 50% of 1.6Ghz and says "ondemand"

When I run programs that use up CPU, CPU0 goes up to 100% , using all of 1.6Ghz available.
However, no matter how many programs I run, CPU1 stays at 50%.

I don't know how to set CPU affinity in ubuntu so I could not test if it's actually true, but is this a hardware problem?

---

### Post by Turboaaa2001 on 2007-07-09
Have you checked to see if there is any throttling bieng done in the BIOS? Anyway thats my 2 cents.

---

### Post by panicb on 2007-07-09
I can't find anything like that in the BIOS. 
It's HP's Pheonix bios..

---

### Post by panicb on 2007-07-09
Problem fixed.

I think the second core stays at 50% if it's on "Ondemand" mode.
It probably shouldn't, but I found the solution:

enable manual cpu freq scaling

in terminal, I typed

sudo chmod +s /usr/bin/cpufreq-selector

then when I left-click on the CPU Frequency Monitor on Gnome-panel, I can switch the modes and the frequency.

---

