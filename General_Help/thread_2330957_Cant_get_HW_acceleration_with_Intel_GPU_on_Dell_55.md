---
title: "Cant get HW acceleration with Intel GPU on Dell 5510"
date: 2016-07-16
forum: General Help
---

### Post by Yaron_Klein on 2016-07-16
[COLOR=#333333][FONT=&amp]Hi, 
Trying to get HW acceleration using Intel GPU.

[/FONT][/COLOR]
```
[COLOR=#333333][FONT=&amp][FONT=&amp]$ /usr/lib/nux/unity_support_test -p[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp][FONT=&amp]libGL error: pci id for fd 4: 8086:191b, driver (null)[/FONT]
[FONT=&amp]i965_dri.so does not support the 0x191b PCI ID.[/FONT]
[FONT=&amp]libGL error: failed to create dri screen[/FONT]
[FONT=&amp]libGL error: failed to load driver: i965[/FONT]
[FONT=&amp]OpenGL vendor string: VMware, Inc.[/FONT]
[FONT=&amp]OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.5, 256 bits)[/FONT]
[FONT=&amp]OpenGL version string: 3.0 Mesa 10.3.2[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp][COLOR=#FF0000][FONT=&amp]Not software rendered: no[/FONT][/COLOR]
[FONT=&amp]Not blacklisted: yes[/FONT]
[FONT=&amp]GLX fbconfig: yes[/FONT]
[FONT=&amp]GLX texture from pixmap: yes[/FONT]
[FONT=&amp]GL npot or rect textures: yes[/FONT]
[FONT=&amp]GL vertex program: yes[/FONT]
[FONT=&amp]GL fragment program: yes[/FONT]
[FONT=&amp]GL vertex buffer object: yes[/FONT]
[FONT=&amp]GL framebuffer object: yes[/FONT]
[FONT=&amp]GL version is 1.4+: yes[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp][FONT=&amp]Unity 3D supported: no
[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp][FONT=&amp]$ sudo lshw -c video[/FONT]
[FONT=&amp][sudo] password for yaronk: [/FONT]
[FONT=&amp]*-display [/FONT]
[FONT=&amp]description: 3D controller[/FONT]
[FONT=&amp]product: GM107GLM [Quadro M1000M][/FONT]
[FONT=&amp]vendor: NVIDIA Corporation[/FONT]
[FONT=&amp]physical id: 0[/FONT]
[FONT=&amp]bus info: pci@0000:01:00.0[/FONT]
[FONT=&amp]version: a2[/FONT]
[FONT=&amp]width: 64 bits[/FONT]
[FONT=&amp]clock: 33MHz[/FONT]
[FONT=&amp]capabilities: pm msi pciexpress bus_master cap_list rom[/FONT]
[FONT=&amp]configuration: driver=nvidia latency=0[/FONT]
[FONT=&amp]resources: irq:16 memory:dc000000-dcffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:e000(size=128) memory:dd000000-dd07ffff[/FONT]
[FONT=&amp]*-display[/FONT]
[FONT=&amp]description: VGA compatible controller[/FONT]
[FONT=&amp]product: Intel Corporation[/FONT]
[FONT=&amp]vendor: Intel Corporation[/FONT]
[FONT=&amp]physical id: 2[/FONT]
[FONT=&amp]bus info: pci@0000:00:02.0[/FONT]
[FONT=&amp]version: 06[/FONT]
[FONT=&amp]width: 64 bits[/FONT]
[FONT=&amp]clock: 33MHz[/FONT]
[FONT=&amp]capabilities: pciexpress msi pm vga_controller bus_master cap_list rom[/FONT]
[FONT=&amp]configuration: driver=i915 latency=0[/FONT]
[FONT=&amp]resources: irq:128 memory:db000000-dbffffff memory:70000000-7fffffff ioport:f000(size=64) memory:c0000-dffff
[/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=&amp][FONT=&amp]$ glxinfo | grep OpenGL[/FONT]
[FONT=&amp]libGL error: pci id for fd 4: 8086:191b, driver (null)[/FONT]
[FONT=&amp]i965_dri.so does not support the 0x191b PCI ID.[/FONT]
[FONT=&amp]libGL error: failed to create dri screen[/FONT]
[FONT=&amp]libGL error: failed to load driver: i965[/FONT]
[FONT=&amp]OpenGL vendor string: VMware, Inc.[/FONT]
[FONT=&amp]OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.5, 256 bits)[/FONT]
[FONT=&amp]OpenGL version string: 3.0 Mesa 10.3.2[/FONT]
[FONT=&amp]OpenGL shading language version string: 1.30[/FONT]
[FONT=&amp]OpenGL context flags: (none)[/FONT]
[FONT=&amp]OpenGL extensions:

[/FONT][/FONT][/COLOR][COLOR=#333333][FONT=&amp][FONT=&amp]$ uname -a[/FONT]
[FONT=&amp]Linux yaronk-ubuntu 4.6.4-040604-generic #201607111332 SMP Mon Jul 11 17:34:50 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/FONT][/COLOR]

```

$ sudo apt-get install -f xserver-xorg-video-intel
[sudo] password for yaronk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 xserver-xorg-video-intel : Depends: xorg-video-abi-15
                            Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.


[COLOR=#333333][FONT=&amp]Since Nvidia drivers are not supported by DisplayLink, need to use the Intel drivers.

Thanks![/FONT][/COLOR]

---

### Post by Yellow Pasque on 2016-07-17
> The following packages have unmet dependencies:
xserver-xorg-video-intel : Depends: xorg-video-abi-15
Depends: xserver-xorg-core (>= 2:1.14.99.902)

Are you running Ubuntu 14.04/Trusty? If not, did you upgrade from Trusty?

> libGL error: pci id for fd 4: 8086:191b, driver (null)
i965_dri.so does not support the 0x191b PCI ID.

So apparently you have a Skylake CPU with integrated HD 530 GPU?

---

### Post by Yaron_Klein on 2016-07-17
Hi,
Thanks for the support!
It looks like I got it to work by installing the packages below.
Should I have tried to install Xenial packages?

Regarding your questions: 
Yes, I starte and still am with Trusty. Then updated the Kernel and packages.
Yes, it's a Skylake CPU with integrated HD530 GPU.

[Update]After trying to switch to Nvidia I get a black screen after reboot. Purged Nvidia and with Intel only [CENTER][COLOR=#000000]:cry:[/COLOR][/CENTER]

```
sudo apt-get install linux-generic-lts-wily xserver-xorg-lts-wily libgl1-mesa-glx-lts-wily libglapi-mesa-lts-wily libwayland-egl1-mesa-lts-wily libgl1-mesa-glx-lts-wily:i386 libglapi-mesa-lts-wily:i386

[COLOR=#333333][FONT=&amp]$ glxinfo | grep OpenGL
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Skylake Halo GT2 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 11.0.2
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 11.0.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:[/FONT][/COLOR]

```

Thanks!

---

### Post by mc4man on 2016-07-17
> **Yaron_Klein said:**
> Hi,
Thanks for the support!
It looks like I got it to work by installing the packages below.
Should I have tried to install Xenial packages?

Regarding your questions: 
Yes, I starte and still am with Trusty. Then updated the Kernel and packages.
Yes, it's a Skylake CPU with integrated HD530 GPU.

[Update]After trying to switch to Nvidia I get a black screen after reboot. Purged Nvidia and with Intel only [CENTER][COLOR=#000000]:cry:[/COLOR][/CENTER]

```
sudo apt-get install linux-generic-lts-wily xserver-xorg-lts-wily libgl1-mesa-glx-lts-wily libglapi-mesa-lts-wily libwayland-egl1-mesa-lts-wily libgl1-mesa-glx-lts-wily:i386 libglapi-mesa-lts-wily:i386


Likely not uncommon for skylake laptops with nvidia gpu (optimus) to not be able to run the nvidia drivers. On my skylake with a GeForce 940M [it's rarely worked]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1565516") on 16.04 over the last 6 months. Just occasionally with the 358 drivers & even then there was an issue. Basically stopped trying as combined with no vsync found the nvidia drivers in an ubuntu session to be a poor experience ( and a hack around to prevent tearing created new issues.
In many regards the Intel gpu provides better performance anyway, currently on 16.04 using mesa 12.1.x which works just fine.

[CODE]OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) HD Graphics 520 (Skylake GT2) 
OpenGL core profile version string: 4.3 (Core Profile) Mesa 12.1.0-devel
OpenGL core profile shading language version string: 4.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 12.1.0-devel
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.1 Mesa 12.1.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
```


As far as 14.04 on skylake I'd only use the 14.04.5 image.

---

### Post by Yaron_Klein on 2016-07-18
Since I'm not going to play with this Laptop no real need for Nvidia.

I now found out that when doing a Skype video call, the video flashes.

---

