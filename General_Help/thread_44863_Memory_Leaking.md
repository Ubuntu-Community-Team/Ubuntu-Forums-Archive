---
title: "Memory Leaking?"
date: 2005-06-27
forum: General Help
---

### Post by uberlinux on 2005-06-27
Hi, I was using KDE with 512 of ram and a 1.6 amd, and it seems like when I would start KDE and log in, memory would go to 130Mb and when surfing the net with firefox, it would steadily increase, until I am at 330+, this seems unreasonable so I switched to XFCE4 with firefox and started at about 62Mb and shot up to 270Mb after about 20min of web with Konqueror, this to seems like a lot for small webstuff, so, does anybody know whats going on?
 ******@blutop:~ $ vmstat -s
 515864 total memory
 432772 used memory
 193048 active memory
 128456 inactive memory
 83092 free memory
 76952 buffer memory
 152984 swap cache
 803240 total swap
 0 used swap
 803240 free swap
 177599 non-nice user cpu ticks
 79 nice user cpu ticks
 16397 system cpu ticks
 466712 idle cpu ticks
 28771 IO-wait cpu ticks
 878 IRQ cpu ticks
 152 softirq cpu ticks
 206548 pages paged in
 323232 pages paged out
 0 pages swapped in
 0 pages swapped out
 7638683 interrupts
 1849914 CPU context switches
 1119915533 boot time
 63650 forks

---

