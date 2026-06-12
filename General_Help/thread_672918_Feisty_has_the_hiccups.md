---
title: "Feisty has the hiccups"
date: 2008-01-20
forum: General Help
---

### Post by Waderider on 2008-01-20
My install of 7.04 has started running erratically in the last 48 hours. Specifically, if I move the mouse pointer across the screen at a steady rate it 'hangs' for a fraction of a second at random, frequent intervals.

At first I presumed a mouse driver issue, but media play back is suffering the same jitter issue, as is typing, as is scrolling through lists.

The system is old but had been running smoothly, Microstar International 6198 mainboard, P3 700Mhz coppermine processor, 368Mb Ram, ATI Rage 128 Pro graphics card, Seagate 30GB HD.

Booting from a live CD of 7.04 the issue doesn't exist. As a footnote I am unable to upgrade to Gutsy from CD or update as the install hangs; this problem always existed, I'm mentioning it to point out upgrading isn't an experiment I can undertake!

This is getting quite annoying as it is affecting the machines usability. I can't pinpoint exactly what changed at the time the problem first occurred because for the first 24hrs I presumed the mouse was dirty.

I've googled this within and without this site and have come up with no clear possible solutions to try. Can anyone help me please?!

---

### Post by bwtranch on 2008-01-20
I don't know, but I've been tol' a green grasshopper got a green asshol.  Yeah, pretty funny.  Well, it's late, what can I say?

Do you have any conflicting apps runnning? Something that might slow the X server down? Try it in terrminal mode and call me in the morning.

---

### Post by kostkon on 2008-01-20
It looks like a Xorg problem or a process that hogs the system down and manages to stay alive even after you reboot. Open a terminal and give
```
top
```
to see what process eats a lot of processor cycles.

---

### Post by Waderider on 2008-01-20
Kostkon, thanks for the reply. 

jeff@jeff-desktop:~$ top

top - 12:40:50 up  1:37,  2 users,  load average: 0.78, 0.77, 0.73
Tasks:  90 total,   1 running,  88 sleeping,   1 stopped,   0 zombie
Cpu(s):  5.7%us,  1.7%sy,  0.0%ni, 92.1%id,  0.0%wa,  0.5%hi,  0.0%si,  0.0%st
Mem:    385932k total,   375900k used,    10032k free,    10720k buffers
Swap:  1124508k total,    31812k used,  1092696k free,   182508k cached

The process list (that I don't seem able to copy and paste) shows no process hogging resources.

As a footnote, I've noticed the issue exists at the log-in screen.

---

### Post by Waderider on 2008-01-20
Bump

---

### Post by Waderider on 2008-01-22
Thought I'd post the solution for those that follow(underwhelmed by the support I received; guess I'm the only person who had this problem!)

Issue disappeared by turning off APM in the Bios. God knows what difference that made! 

Probably caused the problem myself whilst trying to sort a much more minor problem where the computer doesn't fully shutdown when shutdown is selected.........

---

