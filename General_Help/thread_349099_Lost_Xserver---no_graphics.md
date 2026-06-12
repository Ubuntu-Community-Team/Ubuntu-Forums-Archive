---
title: "Lost Xserver---no graphics"
date: 2007-01-29
forum: General Help
---

### Post by PaulFXH on 2007-01-29
After trying to upgrade my nVidia driver (GeForce4 MX 420 card) to allow 3D graphics acceleration, the Xserver failed to start so that I'm now confined to recovery mode.

The problem according to the Xserver log is that there is a mismatch between the driver (1.0-8776) and the nVidia kernel module (1.0-7184)

While installing the driver using
```
 sudo sh NVIDIA-Linux-x86-1.0-8776-pkg1.run
```
the nVidia installer did mention that installing in Runlevel 1 would make it difficult for the kernel module to be configured. This seems to be what happened given the mismatch that now results.

So, I went back into recovery mode and tried to go to Runlevel 3 (typing "telinit 3) at the command prompt. However, this goes through a range of operations in the middle of which the Xserver failure message shows up. Shortly after, the output stops on a line indicating that it is "running various boot scripts". However it goes no further even after 30 minutes of waiting.

I'm puzzled by the appearance of the Xserver message as if this is required to get to Runlevel 3 then I'm in trouble. Indeed, the reason I'm going through this rigmarole is BECAUSE the Xserver won't start.

Can anybody suggest a way out of this to get my kernel module correctly configured?

---

