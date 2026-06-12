---
title: "Ubuntu 18.04 freezes after locking screen"
date: 2018-05-10
forum: General Help
---

### Post by nightmare13 on 2018-05-10
Hi! 
I just installed Ubuntu 18.04 on my computer. Everything works fine but not one thing...
If I lock my pc or let it lock itself, the pc freezes/blocks... sometimes not at the 1st time I lock it, sometimes it's after some locks... Most of times this happens is after letting the pc locked for some time, letting the monitors shutdown....
My setup is: Intel® Core™ i5-8400 CPU @ 2.80GHz × 6 --- 16 GB RAM --- Radeon RX 550
I was thinking that maybe it was related to graphics card... So, instead of using default drivers installed by Ubuntu, I installed the drivers from AMD. But I still have the same problem
Does someone have the same problem?
How can I fix this? 
Thanks in advance

---

### Post by pmadr2 on 2018-06-28
Hi,

I have exactly the same problem. I have 4k monitor connected by HDMI.
CTRL+F4 works, I can login to shell.
CTRL+F1 returns me to the purple screen. It seems not to be frozen, only mouse and login window is not displayed, so I can't login to GNOME.

---

### Post by pmadr2 on 2018-06-29
Progress done. It seems to be connected with 2 monitors. Ubuntu detected 2 monitors but I have just 1. It's the 2nd in Ubuntu settings and it's the problem.
 The lock screen works fine but the window for sign up is placed on 1st **not active** monitor. Ubuntu thinks that it's the main monitor. So I changed monitors to Single Display.

---

### Post by FoolInTheRain on 2018-10-10
Same problem.

Installed 18.04 last week and I'm getting a constant problem with my computer just totally locking up randomly.

The ONLY remedy is a reboot

---

### Post by wildmanne39 on 2018-10-10
Hello FoolInTheRain, please start your own thread if you need support for this issue.

Thanks

---

