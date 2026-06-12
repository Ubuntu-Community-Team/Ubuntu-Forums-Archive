---
title: "Just upgraded from 13.04 to 13.10 - Intel Graphic driver installer"
date: 2013-10-20
forum: General Help
---

### Post by lobosuelto on 2013-10-20
So I just upgraded to Ubuntu 13.10 64 bit on a Dell laptop. Regular computer with integrated graphics card. In 13.04 I was able to instll the Intel graphics drivers. 
Now the Software center wont let me: libpackagekit-glib2-14 dependency not satisfied.
Should I wait till Intel launches a driver installer for 13.10?

---

### Post by pqwoerituytrueiwoq on 2013-10-20
intel gpus don't require any special drivers, they just work
if you want a newer one give the mainline kernel a try
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)

---

### Post by xdealmeida on 2013-10-20
Yes they worked by default but will they have vaapi support and all the right librairies to HW decoding etc....?

---

### Post by lobosuelto on 2013-10-20
> **pqwoerituytrueiwoq said:**
> intel gpus don't require any special drivers, they just work
if you want a newer one give the mainline kernel a try
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme)

If there's no point in installing Intel graphics drivers, then why does Intel ship the Intel graphic driver installer for Ubuntu?
And, I keep getting these messages in Software Center what won't let me install some programs. Dependencies issues.

---

### Post by philinux on 2013-10-20
I don't think they've caught up with 13.10 yet. Also there's Mir in the mix .

[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)

My acer 1410 is running mir fine on a default install. In 13.04 I found no difference running the Intel installed drivers. YMMV.

---

### Post by xdealmeida on 2013-10-20
[B]Without Intel drivers, all looks good by default. That may mean that now ubuntu ships with decent intel drivers support! cool

[/B]OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Desktop 
OpenGL version string:  3.0 Mesa 9.2.1


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes

  *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

---

### Post by lobosuelto on 2013-10-20
Whats the command for that?

> **xdealmeida said:**
> [B]Without Intel drivers, all looks good by default. That may mean that now ubuntu ships with decent intel drivers support! cool

[/B]OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ivybridge Desktop 
OpenGL version string:  3.0 Mesa 9.2.1


Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       yes

  *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:48 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

Whats the commmand for that?

---

### Post by flay2 on 2013-10-20
I'm having the exact same problem as lobosuelto. Tried upgrading from 13.04, faced a few issues, did a clean reinstall of 13.10
Now I cant get out of software rendering mode and my resolution is very very low.

Tried installing the intel driver update utility, yielded this message
 libpackagekit-glib2-14 dependency not satisfied

I have an asus u46e. Graphics are intel hd 3000.

Any ideas?

---

### Post by xdealmeida on 2013-10-21
Try this!

/usr/lib/nux/unity_support_test -p

I have vlc working with HW decode etc... so no much an issue but I was wondering if Intel Graphics drivers are or will still be necessary if by default there is a good intel video support

libva info: VA-API version 0.34.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_34
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.34 (libva 1.1.1)
vainfo: Driver version: Intel i965 driver - 1.2.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Simple            :	VAEntrypointEncSlice
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointEncSlice
      VAProfileH264Baseline           :	VAEntrypointVLD
      VAProfileH264Baseline           :	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileJPEGBaseline           :	VAEntrypointVLD

you should raise you concerns about the installer here I assume:
[https://01.org/linuxgraphics/node/237](https://01.org/linuxgraphics/node/237)

---

### Post by lobosuelto on 2013-10-21
/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string:  2.1 Mesa 9.2.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


Does that mean I need no Intel graphics installer? My only concern is that in 13.04 the alt+tab animations, and the Super+W window display seemed smoother (had the intel graphics drivers installed). It does seem a bit laggy now ... 
(apart from that, Compiz process is consuming almost 200 MB of RAM. **** got resource hungry as hell. Strangely, its trigered by I-don't-know-what, because it goes from consuming around 50 MB to 190 MB when the computer's been on for lets say a half hour. Seems that unity-scope-lens is the process that trigers the memory "leak")

---

### Post by fritzophrenic on 2013-10-26
> **pqwoerituytrueiwoq said:**
> intel gpus don't require any special drivers, they just work

They really, really don't: [http://askubuntu.com/questions/335124/flash-player-a-big-bug](http://askubuntu.com/questions/335124/flash-player-a-big-bug)

I went to go get the driver to fix an issue making YouTube and Hulu and anything else using Flash completely unusable. I wasn't expecting the dependency issue. So...wait for Intel to come out with new drivers is the name of the game? I didn't see any other solutions mentioned besides "try the bleeding-edge kernel" which I'm certainly NOT planning to try. This old computer is too hard to maintain as it is.

---

### Post by gratzie on 2013-11-02
Thank you very much for the oinformation: with this command: "/usr/lib/nux/unity_support_test -p" i get this:
OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 9.2.1

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

### Post by gratzie on 2013-11-03
/usr/lib/nux/unity_support_test -p

---

### Post by roiikkata on 2013-11-21
intel said to sit tight. the driver updates will probably just pop up in the update manager when they release them for this new 13.10 ..

---

### Post by roiikkata on 2013-11-28
i just moved back to 12.04 and the intel errors stopped. they werent happening in 13.04 but 12.04 is the stable release, so ..

---

### Post by mörgæs on 2013-11-28
Some (older) Intel cards need an [xorg.conf]("https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html") under 13.10.

---

### Post by Bashing-om on 2013-11-28
et al;

For those running 13.10 with graphics problems, this has recently come to my attention. It may be a benefit to those running Intel, Nvidia or ATI cards.

Updated and Optimized Open Graphics Drivers Supported Ubuntu versions:- 13.10 :
[https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

