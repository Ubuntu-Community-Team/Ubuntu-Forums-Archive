---
title: "unable to identify the cause for high virtual memory usage."
date: 2015-12-28
forum: General Help
---

### Post by arul1694 on 2015-12-28
In my vps there is  high usage of virtual memory(currently 30%,some time's even more), is it normal?

I am unable to find the cause for high virtual memory usage,i am currently  running seedbox with torrentflux-ng, and rapid leech for personal use only, and wordpress blog.

specifications of my vps are:
[TABLE="class: table table-hover"]
[TR]
[TD]**Operating system**[/TD]
[TD]Ubuntu Linux 14.04.3[/TD]
[/TR]
[TR]
[TD]**Webmin version**[/TD]
[TD]1.770[/TD]
[/TR]
[TR]
[TD]**Theme version**[/TD]
[TD] Authentic Theme 16.01  [/TD]
[/TR]
[TR]
[TD]**Time on system**[/TD]
[TD]Mon Dec 28 07:02:52 2015[/TD]
[/TR]
[TR]
[TD]**Kernel and CPU**[/TD]
[TD]Linux 2.6.32-32-pve on x86_64[/TD]
[/TR]
[TR]
[TD]**Processor information**[/TD]
[TD]Intel(R) Xeon(R) CPU           X5660  @ 2.80GHz, 4 cores[/TD]
[/TR]
[TR]
[TD]**System uptime**[/TD]
[TD]2 days, 20 hours, 31 minutes[/TD]
[/TR]
[TR]
[TD]**Running processes**[/TD]
[TD]40[/TD]
[/TR]
[TR]
[TD]**CPU load averages**[/TD]
[TD]0.19 (1 min) 0.07 (5 mins) 0.01 (15 mins)[/TD]
[/TR]
[TR]
[TD]**Real memory**[/TD]
[TD]1.95 GB total / 167.74 MB used[/TD]
[/TR]
[TR]
[TD]**Virtual memory**[/TD]
[TD]500 MB total / 133.05 MB used[/TD]
[/TR]
[TR]
[TD]**Local disk space**[/TD]
[TD]313.56 GB total / 246.93 GB free / 66.63 GB used[/TD]
[/TR]
[TR]
[TD]**Package updates**[/TD]
[TD]All installed packages are up to date [/TD]
[/TR]
[/TABLE]

---

### Post by gordintoronto on 2015-12-28
The command "top" might help you identify how memory is being used. I would have expected a much larger virtual memory, maybe 4 GB. Linux often "rolls out" seldom-used memory to the swap. Your real memory usage is very low, so I would not worry about the swap.

Why is your kernel so old?

---

