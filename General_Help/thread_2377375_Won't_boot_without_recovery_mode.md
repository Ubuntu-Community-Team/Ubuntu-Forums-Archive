---
title: "Won't boot without recovery mode"
date: 2017-11-12
forum: General Help
---

### Post by sir.jay on 2017-11-12
Apparently a lot of people have been posting about this issue but I don't really see an answer. When I install the proprietary graphics driver on Ubuntu or any of it's official flavours I immediately am not able to boot the system without the use of recovery mode. So it's obviously a graphics problem of some kind because it doesn't happen otherwise. I just don't have any idea what kind of graphics problem. I use a pretty common video card which is the Nvidia GeForce GTX 750 Ti and I use the flavour of Ubuntu, Xubuntu 17.10. Anyone know the answer to this problem and how to fix the issue?

---

### Post by benjimenez805 on 2018-02-14
What has happen to me in the past is that the new video driver doesn't set the resolution correctly, so when you reboot it tries to set your monitor to a resolution that it doesn't support. In my case I was using an ATI Radeon driver so I just used the aticonfig command to fix the problem like so.

I entered this from the command line.

aticonfig resolution=0,1024x768

This set my resolution to something I knew my monitor supported.
Your problem may be a similar one which is common when changing drivers in linux

---

### Post by QIII on 2018-02-14
aticonfig has nothing to do with NVIDIA.  aticonfig is no longer supported in 16.04 or later.  This thread hasn't been visited by the OP in quite some time.

---

