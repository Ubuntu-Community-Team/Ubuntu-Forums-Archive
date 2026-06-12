---
title: "Screen flashing white in terminal (tty) with Nvidia 340.65 driver."
date: 2015-01-07
forum: General Help
---

### Post by Gunther_Van_Dooren on 2015-01-07
Hi there,

I have Ubuntu 14.4 installed with the Nvidia 340.65 driver from ppa:xorg-edgers/ppa selected true the "additional drivers" tool.
This is the guide i folowed: [http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

The first problem i had was that my graphical desktop was flickering. I have solved that with this fix:
[http://ubuntuforums.org/showthread.php?t=2243912&highlight=nvidia+flickering](http://ubuntuforums.org/showthread.php?t=2243912&highlight=nvidia+flickering)

Now i have 1 problem left, if i press ctrl+alt+F1 my screen starts to flash. The same hapens with all the TTY's except for TTY7 wich restores my desktop.
Allso when i shytdown my pc the flasshing aprears till it powers off. Here is a video of what hapens. In the video i press ctrl+alt+F1 then back to ctrl+alt+F7
[http://www.youtube.com/watch?v=FIpn7CNv-gc&feature=youtu.be](http://www.youtube.com/watch?v=FIpn7CNv-gc&feature=youtu.be)

Then finaly some additional info:

```

lspci -vnn | grep -i VGA -A 12
returns:

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114M [GeForce GTX 670M] [10de:1213] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:fb18]
    Flags: bus master, fast devsel, latency 0, IRQ 48
    Memory at d0000000 (32-bit, non-prefetchable) [size=32M]
    Memory at c0000000 (64-bit, prefetchable) [size=128M]
    Memory at c8000000 (64-bit, prefetchable) [size=64M]
    I/O ports at 3000 [size=128]
    [virtual] Expansion ROM at cc000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia

01:00.1 Audio device [0403]: NVIDIA Corporation GF114 HDMI Audio Controller [10de:0e0c] (rev a1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]

```
```

glxinfo | grep OpenGL | grep renderer
returns:

OpenGL renderer string: GeForce GTX 670M/PCIe/SSE2

```

I been searching for a while now, I cannot find a propper solution.
So i wonder if someone got a idea how i can fix this.

---

### Post by Gunther_Van_Dooren on 2015-01-08
Realy noone?

---

### Post by Godwyn on 2015-01-15
I Still have this problem. anyone else got it or had it?

---

