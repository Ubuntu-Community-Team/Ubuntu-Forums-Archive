---
title: "Is there any way to solve the Graphics question on an Optimus/hybrid GPU system?"
date: 2017-02-27
forum: General Help
---

### Post by bendyke on 2017-02-27
Dear sweet baby Ubuntu folks!

I recently reinstalled Ubuntu on my new ACER Aspire E 15, which comes with a hybrid GPU setup, giving me an integrated Intel video card and a dedicated nvidia geForce 840M. I have tried installing numerous graphics drivers, before realising the Nvidia drivers alone won't be enough and it will always just give me a login loop until I revert with 
```
sudo apt-get purge nvidia-*
```. 

I tried the Bumblebee method with little success (it kept giving me an error every time I tried running anything in 'optirun', which I wasn't able to fix) until I managed to wreck my install completely and had to reinstall Ubuntu. 
As of right now, I am using the X.Org Nouveau drivers, which doesn't even seem to use my integrated Intel video card, because I tried playing a blu ray quality video in VLC and it kept clipping the image lines, so obviously lacking speed which even an integrated Intel GPU should be able to handle. 
It's giving me 2 alternative NVIDIA drivers, 167.57 and 340.101 , I have tried using both with no success.

So I am placing my faith in you guys, hopefully you can help me. Is there ANY other possible way to get the nvidia GPU up and running successfully in 16.04? It's a shame that bomb GPU is just sitting there and without the GPUs the experience is a little sub par (slow). 

Thanks in advance :)

---

### Post by mc4man on 2017-02-27
The nvidia gpu you have may need newer than 340.101
Putting that aside you may get as good or better video playback with the Intel iGPU plus nvidia drivers will likely cause tearing, at least when used thru the default of nvidia-prime

So to that end maybe provide a little more info - 
```
sudo apt-get install mesa-utils inxi vainfo
```
Then post results of these

```
glxinfo |grep OpenGL
```
```
inxi -b
```
```
vainfo
```

---

### Post by bendyke on 2017-02-28
Here are the results for all the codes:

```
don@don-Aspire-E5-571G:~$ glxinfo |grep OpenGL
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 12.0.6
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 12.0.6
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 12.0.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
don@don-Aspire-E5-571G:~$ 
```

```
don@don-Aspire-E5-571G:~$ inxi -b
System:    Host: don-Aspire-E5-571G Kernel: 4.4.25-040425-generic i686 (32 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Acer model: EA50_HB v: V1.31
           Bios: Insyde v: V1.31 date: 08/03/2015
CPU:       Dual core Intel Core i5-5200U (-HT-MCP-) speed/max: 2200/2700 MHz
Graphics:  Card-1: Intel Broadwell-U Integrated Graphics
           Card-2: NVIDIA GM108M [GeForce 840M]
           Display Server: X.Org 1.18.4 drivers: fbdev,intel (unloaded: vesa)
           Resolution: 1366x768@76.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
           GLX Version: 3.0 Mesa 12.0.6
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           Card-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k
Drives:    HDD Total Size: 500.1GB (10.2% used)
Info:      Processes: 237 Uptime: 2:34 Memory: 1480.3/3961.5MB
           Client: Shell (bash) inxi: 2.2.35 
don@don-Aspire-E5-571G:~$ 


```


```
don@don-Aspire-E5-571G:~$ vainfo
libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns -1
libva error: va_getDriverName() failed with unknown libva error,driver_name=(null)
vaInitialize failed with error code -1 (unknown libva error),exit
don@don-Aspire-E5-571G:~$ 

```


From what I can tell, Ubuntu recognises both GPUs (which is good), but  doesn't seem to be utilising either of them with the current driver. I'm  committed ot using Ubuntu now, because it's so much more accessible  than pretty much any other OSes, so getting the GPUs up and running is  an important step :razz: 

Thanks again :smile:

---

### Post by mc4man on 2017-02-28
```
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
```
That will be a terrible user experience. Maybe you should go to the HWE Kernel/xserver as Broadwell could have issues with the 4.4 kernel, see here under the Ubuntu 16.04 LTS - Xenial Xerus section > Desktop 
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Or just do a fresh install using the latest image, (16.04.2 image) - [https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop) This will give you the 4.8.x kernel, ect.

---

### Post by bendyke on 2017-03-01
I installed the newest kernel, but the OpenGL renderer is still the same, with no new available drivers and no observable improvement in user experience. (video still produces clipping). 

```
don@don-Aspire-E5-571G:~$ inxi -b
System:    Host: don-Aspire-E5-571G Kernel: 4.8.0-39-generic i686 (32 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Acer model: EA50_HB v: V1.31
           Bios: Insyde v: V1.31 date: 08/03/2015
CPU:       Dual core Intel Core i5-5200U (-HT-MCP-) speed/max: 1148/2700 MHz
Graphics:  Card-1: Intel Broadwell-U Integrated Graphics
           Card-2: NVIDIA GM108M [GeForce 840M]
           Display Server: X.Org 1.18.4 drivers: fbdev (unloaded: vesa)
           Resolution: 1366x768@76.00hz
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
           GLX Version: 3.0 Mesa 12.0.6
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           Card-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k
Drives:    HDD Total Size: 500.1GB (6.1% used)
Info:      Processes: 234 Uptime: 3 min Memory: 1074.3/3959.8MB
           Client: Shell (bash) inxi: 2.2.35 

```

```
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 12.0.6
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 12.0.6
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 12.0.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
```

Is there any other way I can make it work? Otherwise without a functioning GPU I may have to just suck it up and move back to windows, as **** as it is. i'd much rather solve this then crawl back to Bill Gates though :/

---

### Post by Geoffrey_Arndt on 2017-03-02
Maybe worth a try - - - Ubuntu 16.10 or even 17.04 beta1?    What to lose?

---

### Post by bendyke on 2017-03-02
> **Geoffrey_Arndt said:**
> Maybe worth a try - - - Ubuntu 16.10 or even 17.04 beta1?    What to lose?

What exactly could that accomplish? Surely if there were any new drivers, they would be available on the 16.04 LTS and the newest official kernel. 
As far as I know, bumblebee seems to be working for most people, maybe I'm doing something wrong with it, but considering how last time I tried I was unable to purge the wrong drivers and had to do a reinstall, I'm wary about trying it again.
It hurts my soul, but I think Ubunu just isn't versatile enough to accommodate laptops like mine with unconventional setups, especially when it comes to graphics cards. I don't want to move back to windows, unless it's my only option left.

---

### Post by mc4man on 2017-03-03
Don't have a Broadwell machine so can't compare, Haswell & Skylake work fine here. Just to ck. somethings - 
This should  return just a long list of "Installed: (none)"
```
apt-cache policy nvidia* |grep Installed
```

Likely this will show some fails?
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by bendyke on 2017-03-03
> Likely this will show some fails?
```
/usr/lib/nux/unity_support_test -p
```
  
Yeah the first line gives a long list of nones.
The second line gives me this:

```
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)
OpenGL version string:  3.0 Mesa 12.0.6

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

---

### Post by Geoffrey_Arndt on 2017-03-03
Is there a particular reason for running a 32bit kernel on this laptop?   Does the hybrid gpu require 32 bit versus 64?   

(EDIT sorry, . . . it seems it may . . . which, if so, removes the possibility to run the very latest advanced distros (Elementary/Antergos/Solus, etc.).

(EDIT2 . . am also assuming you've tried the workarounds for 32 bit on 64 bit hardware at:   [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee))

---

### Post by bendyke on 2017-03-03
> **Geoffrey_Arndt said:**
> Is there a particular reason for running a 32bit kernel on this laptop?   Does the hybrid gpu require 32 bit versus 64?   

(sorry, . . . I've never owned that type of system as I opt for System76 hardware the last few years . . takes all of 10 minutes to set up and then runs smoother than a baby's butt).

Not really, other than the fact that that's the image I used for my older laptop. Should I try to burn a 64-bit version? And could that help things? I know I'M being a pain, I just realised anything you do on Ubuntu can wreck your entire installation easily :D Cheers

---

### Post by Geoffrey_Arndt on 2017-03-03
Please see my edited response.   In that link the key part is 2/3rd of the way through the wiki article . . "**Error running 32-bit applications on a 64-bit system"**


So refer to the link and if you've haven't tried this workaround . . then it's worth a shot.

---

