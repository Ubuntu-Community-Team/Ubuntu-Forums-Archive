---
title: "Problems shutting off Ubuntu 20.04.3 LTS"
date: 2022-01-30
forum: General Help
---

### Post by pets71 on 2022-01-30
Hey!
Just to start, here's my current hardware:
Lenovo ideapad 330-17ast
AMD A4-9125 with Radeon R3 graphics
8GB ram, replacement 
240GB SSD, instead of the original 1TB HDD
and software:
Ubuntu 20.04.3 LTS
Kernel 5.13.0-27-generic
amdgpu v.19.1.0-1, not sure about this one, got it with apt list --installed | grep -i amdgpu

Well to the actual problem. For the last month or so, every time i turned off my computer or put it to standby, the screen just turned off, the whole thing goes unresponsive, and the power indicator stays on. This state would stay until i forced a shutdown by holding down the power button. (Once i left the computer on this state overnight and it was still the same in the morning) I know it isn't a power led problem, the fans also still spin, and this also occurs when downloading updates that need to restart, and the whole thing just locks up for hours, and i have to force the shutdown once again, which has caused some serious problems. I've tried searching for answers to this problem online, but every time I've found the same problem, there has never been a solution for it that works. I tried fixing this whole thing with a friend whose better at these sorts of things, but the only thing that worked was by the grub parameter nomodeset, which really isn't a long term answer, since it really tanks the computers performance, and I lose brightness control and standby mode still does the same thing. But from this, we pretty much gathered that its something to do with the gpu-driver, but of course I'm not a hundred percent certain. Fairly new to the whole Linux thing so I'm not so sure what to do, so wanted to ask about it here. Any fixes or should I just get a newer laptop when the performance gets unbearable? I can send logs and stuff if necessary. Thanks in advance!

---

### Post by pets71 on 2022-02-02
Updated yesterday and the problem is gone.

---

