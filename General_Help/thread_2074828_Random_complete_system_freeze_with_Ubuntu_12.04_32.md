---
title: "Random complete system freeze with Ubuntu 12.04 32bit"
date: 2012-10-22
forum: General Help
---

### Post by sprungfeld33 on 2012-10-22
Hi,

for 4 weeks now, I have been running Ubuntu 12.04 on a brand new Lenovo Thinkpad T530. For the first three days, I had the 64bit Version of 12.04 installed, which froze randomly every 10hours or so. I updated the Kernel, which fixed the problem, but lead to driver problems. After 3 days of frustration, I installed the 32bit version of 12.04 - wich ran _TOTALLY_ (and i mean: TOTALLY) smooth until this morning.

Since this morning, I had 4 total system freezes, every 2 hours or so. This is completely unexplainable to me. I changed _NOTHING_. I did not even install anything in the past three days. The machine ran ~18hours a day without any problem for the past 25 days, not even a single freeze, and now, all of a sudden, I get freezes every 2 hours. :(

I am talking about total system freezes here. The mouse is not working and I cannot CTRL-ALT-Fx. I tried to connect the freezes to an application, but they occur randomly.

There is no error message in the syslog, it ends with some random info messages minutes before the crash and begins with the boot messages. Nothing in between, so I am suspecting a kernel panic.

Please help :(

---

### Post by peterdordal on 2012-11-26
I too am running Ubuntu 12.04 on a Lenovo T530. I too first installed  64-bit linux, only to have the system crash (that is, freeze, with the  screen intact) 2-3 times/day.

When I switched to 32-bit linux, the system crashed less often: maybe once every 2-3 days.

For what it's worth, the crash distribution doesn't seem to be Poisson (that is, random).

I have two theories:
1. A hardware flaw or misconfiguration, possibly intermittent
2. A problem with the video driver (I do have the 1920x1080 display)

When I have time, I plan to see what can be done to monitor kernel panics.

---

### Post by abrianb on 2012-12-28
Does this bug look like the problem you are having?
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

---

### Post by Pjotr123 on 2012-12-28
Brand new hardware: try Ubuntu 12.10. Even though it's not an LTS, it does contain the newest drivers.

---

