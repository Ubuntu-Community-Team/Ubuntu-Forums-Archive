---
title: "Second HDMI monitor turning off then on again every x minutes"
date: 2024-07-02
forum: General Help
---

### Post by ernecastro on 2024-07-02
Hey everyone,

I have a long lasting problem, it started way back when I was using Manjaro. Four months ago I switched to Ubuntu for this specific issue, and everything was fine. But now one week ago I started having the same issue.

The problem is that one of my two monitors, every so often, it turns off and then immediately back on, as if it would lose signal for a second or so. This does not happen with Windows, so although my setup could be a factor, I don´t think I have bad hardware.

Any idea how I can troubleshoot and solve this problem?

My setup is

[LIST]
[*]Ubuntu 24.04 (default setup)
[*]Dell XPS 13 (Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz)
[*]Intel Corporation UHD Graphics 620 (rev 07)
[*]Pluggable Thunderbolt 3 dock station
[*]2 x Asus VZ239
[/LIST]

---

### Post by ernecastro on 2024-07-05
It seems that I managed to fix the issue. Changing the refresh rate from 60Hz (default) to 59.94Hz fixed the problem.

For some reason one of the monitors defaulted to 59.94Hz and the other to 60Hz, they are both the same, I bought them at the same time.

---

