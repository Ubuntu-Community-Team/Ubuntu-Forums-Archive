---
title: "suspend on dell dimension 8400 with nvidia graphics"
date: 2008-06-05
forum: General Help
---

### Post by theproc64 on 2008-06-05
When I try to suspend on my dimension 8400, it goes into suspend fine but doesn't display anything when I try to wake it up (monitor doesn't even detect input). I have a geforce 8500gt using the nvidia driver and have compiz enabled. Does anyone have a solution or just anything I can try?

---

### Post by cprofitt on 2008-06-06
> **theproc64 said:**
> When I try to suspend on my dimension 8400, it goes into suspend fine but doesn't display anything when I try to wake it up (monitor doesn't even detect input). I have a geforce 8500gt using the nvidia driver and have compiz enabled. Does anyone have a solution or just anything I can try?


This is an issue with the -17 and -18 kernels there is a potential fix that will come with the -19 kernel. If you need suspend and still have the -16 kernel you should be able to use that one with success.

[https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/226279](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/226279)

---

### Post by theproc64 on 2008-06-20
with the -19 kernel suspend works great the first time, after that, it resumes to a blank screen and you need to restart xserver to getr back.  It only works great the first time you suspend after an xserver start.

---

