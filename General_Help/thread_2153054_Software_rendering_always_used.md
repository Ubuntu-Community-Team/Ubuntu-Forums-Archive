---
title: "Software rendering always used"
date: 2013-06-10
forum: General Help
---

### Post by tarshoduze on 2013-06-10
Hi,
It seems that software rendering is used in my Xubuntu 12.10.
Here's what glxinfo says (relevant parts only):
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/i386-linux-gnu/dri/swrast_dri.so
...
direct rendering: Yes
server glx vendor string: SGI
...
client glx vendor string: Mesa Project and SGI
...
OpenGL vendor string: VMWare, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
...

I have an onboard Intel 82865g graphics.

I dualboot with (god forbid) Windows XP SP3, and I must say I can run Fusion (the Sega Genesis emulator) with up to 60FPS, and Grand Theft Auto III with playable FPS (I guess around 20 to 30). With Xubuntu 12.10, I only get 25FPS (with compositing enabled) or 30FPS (with compositing disabled). It is also worth mentioning that my CPU usage (Pentium IV single-core, 2.6GHz) is 100% while using Fusion, while it is just around 50% in Windows.
I know my graphics is not that bad. How do I enable hardware rendering?

---

### Post by 3rdalbum on 2013-06-10
If you are running Xubuntu in a virtual machine, you can't expect to get good 3D performance. If you haven't already, install the VMware guest additions that will speed up your 3D a little bit in the guest operating system.

---

### Post by tarshoduze on 2013-06-11
Thanks for the reply, but no, I am using Xubuntu natively.
It seems to be using software rendering for OpenGL... ZSNES runs fine, though. I guess ZSNES doesn't use OpenGL.
I'm very comfortable with terminals.

---

