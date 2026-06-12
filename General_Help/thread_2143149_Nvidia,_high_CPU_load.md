---
title: "Nvidia, high CPU load"
date: 2013-05-08
forum: General Help
---

### Post by Edenhard on 2013-05-08
Dear all,

I installed ubuntu 13.04 with unity, but it occupied so much CPU and the temperature is a little high. Then I use the command 'sudo apt-get install xfce' to install XFCE. But it seems no improvement and here is the details:

cpu1:5.0%,cpu2:0.0%,cpu3:4.0%,cpu4:1.0%

Memory:4419MiB(11.8%) of 3.7 GiB

My CPU is:inter coreTM i5-2520M CPU @2.5GHz.

Could you tell me why and how to deal with it?  Is it related to the NVIDIA deriver for graphics is not installed?

Thanks!

---

### Post by mastablasta on 2013-05-08
very likely. if you have nvidia chip or if this is hybrid graphics (and it looks like it is) you need to install nvidia driver. if it's hybrid graphics (a.k.a nvidia Optimus you need to look at project bumblebee for solution.

---

### Post by Edenhard on 2013-05-08
Thanks so much!
I have tried to install the NVIDIA driver but failed. After installing the driver and restart, then the window has no bar and the resolution is lower than normal.

---

