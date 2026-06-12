---
title: "Intel HD graphics 3D acceleration"
date: 2013-02-21
forum: General Help
---

### Post by projectrk on 2013-02-21
hi guys,

im new to this too, im using ubuntu 12.04 with intel i7 intel graphics hd 2000 series.

found this link [https://01.org/linuxgraphics/downloads/2012/2012q4-intel-graphics-stack-release](https://01.org/linuxgraphics/downloads/2012/2012q4-intel-graphics-stack-release) in one of the post here, but i don't know which is which to download. i just want to optimize my video with 3d acceleration enabled. what should i do? whats the step by step process for this? can anyone help please. thank you very much in advance

---

### Post by codemaniac on 2013-02-21
Moved to its own thread.

---

### Post by Cheesemill on 2013-02-21
With Intel drivers there is usually nothing to do. The correct drivers are installed with Ubuntu and used automatically.

---

### Post by Impavidus on 2013-02-21
If you've got very recent hardware the drivers may be unavailable in your kernel version, which leads to 3D acceleration being unavailable. This is assuming you use the 3.2 kernel. In this case you can upgrade to 12.10 (or just install the 3.5 kernel, nowadays available for 12.04 too).

---

### Post by cherep on 2013-04-14
Hi all,
I have a similar problem. I used Ubuntu 10.10 and all 3d effects were working on my intel integrated graphic card (3000 series).

I'm currently running 12.04.2 LTS and see no video acceleration at all. How do I know it: When I press "Super" button, the help with unity shortcuts is not appearing. Surprisingly, video acceleration works when I boot from the ubuntu 12.04.2 live cd :)!

Question: how can I activate video acceleration on my ubuntu 12.04.2 installed?

```
lspci -v | less
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated G
raphics Controller (rev 12) (prog-if 00 [VGA controller])
        Subsystem: Lenovo Device 3920
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 1800 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

```

```

/usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0".
Error: GLX is not available on the system

```

```

sudo gedit /etc/X11/xorg.conf
Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection
```

---

### Post by cherep on 2013-04-14
ok, I found a solution [here]("http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work").
I do also have nvidia, and this could cause some problems. So one should run:
```

sudo apt-get purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx libglapi-mesa libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg
sudo reboot

```
then it will work fine with the intel graphic card. To get optimus running, install bumbleebee from [link]("http://bumblebee-project.org/install.html#Ubuntu").

---

