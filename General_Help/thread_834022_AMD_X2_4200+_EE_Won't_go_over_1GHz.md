---
title: "AMD X2 4200+ EE Won't go over 1GHz"
date: 2008-06-19
forum: General Help
---

### Post by Tekno_Cowboy on 2008-06-19
I'm having the problem of my CPU getting stuck at a lower speed than full. I don't notice it most of the time, but I really notice it when I try to play a video. It will throttle up just long enough to catch up, then throttle down until it gets stuck again. 

I havn't run Ubuntu in a while, but I remember having the same problem in Gutsy when it first came out. I fixed it by disabling a service, but I can't remember which service, or at what run levels it was at.

Could someone please refresh my memory, or give me an alternative solution?

---

### Post by sdennie on 2008-06-19
Can you post the output of:

```

cpufreq-info

```

(You may have to install it first)

---

### Post by Tekno_Cowboy on 2008-06-19
Thanks, that was enough to let me figure out how to turn off the cpu scaling. Thanks!

---

