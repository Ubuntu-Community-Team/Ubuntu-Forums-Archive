---
title: "GUI works fine on LiveCD, but it becomse very slow after installing it"
date: 2021-06-18
forum: General Help
---

### Post by guilleing on 2021-06-18
I'm having problems with a fresh install of Ubuntu 20.04 LTS.


I decided to install a new ssd on my laptop. It's a Lenovo G480 (i5 processor, 8GB of RAM and integrated Intel graphics). So I took out the old hdd and installed this new ssd. Then I went on to install Ubuntu 20.04 LTS.
I booted with a LiveCD. There, the OS runs smooth (note: I had to boot with nomodeset or 'safe graphics mode', otherwise it won't boot). But after installing and rebooting to the new installation, the graphical interface is extremely slow.


I tried Ubuntu Mate and Xubuntu as well, just to see if it was a problem with the default GUI of Ubuntu.
On all these distros I have the same problem: on LiveCD the UI is smooth, but after installing, this fresh install GUI is very slow. For example, watching a youtube video is impossible.
On "Additional drivers" there are no proprietary graphic drivers available.
My previous OS was Ubuntu 18.04 iirc and I didn't have this problem.


[Here's a small video I recorded when I tried Xubuntu.]("https://imgur.com/a/6e3RmSe")

[On the login screen there's no option to change between Wayland and Xorg.]("https://imgur.com/a/cvjPbhN")

Any ideas on what could be happening here? Thanks in advance!


Here's the output of some commands (sorry for the bad formatting):

```

$ lshw -c video
  
*-display UNCLAIMED
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2[/FONT][FONT=courier new]
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:3000(size=64) memory:c0000-dffff


$ swapon

NAME      TYPE      SIZE USED PRIO
/dev/dm-2 partition 976M   0B   -2


$ sudo dmidecode -s bios-version

5ECN95WW(V9.00)


```

---

### Post by QIII on 2021-06-18
guilleing --

Please use the default font and color unless you have a good reason to draw attention to a particular part of your post.

Also, please enclose all terminal commands and their results in code tags, which will preserve the formatting and make your post easier to read.

To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by guilleing on 2021-06-18
Thanks! Sorry for the formatting. It got messed up and I wasn't able to get it back to normal.

---

### Post by grahammechanical on 2021-06-18
The live session runs fine because you are using the nomodeset option which tells the installer not to load a video driver but to use the BIOS video modes.

> Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded.

[https://askubuntu.com/questions/207175/what-does-nomodeset-do](https://askubuntu.com/questions/207175/what-does-nomodeset-do)

The printout from the command:

```
lshw -c video
```

reveals that installed Ubuntu is not using a video driver. And that is why the video quality is so poor. When I run that command I see this:

>   *-display                 
       description: VGA compatible controller
       product: GT216 [GeForce GT 220]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:31 memory:fd000000-fdffffff memory:c0000000-cfffffff memory:dc000000-ddffffff ioport:8c00(size=128) memory:c0000-dffff

Notice, that the video driver is Nouveau. It is an open source video driver. If we are connected to the internet when we load Software & Updates>Additional Drivers we should get the option to use the standard open source video driver (Nouveau) or a proprietary video driver. And I do not know why you are not getting that option.

If we install Ubuntu and tick a box to install non-free software we get some audio and video codecs and a proprietary video driver. Oh, by the way, Ubuntu 20.04 defaults to using the X-server.

Regards

---

### Post by guilleing on 2021-06-18
Thanks for the reply. Isn't Noveau for Nvidia cards? AFAIK my laptop (Lenovo G480) only has an integrated intel graphics card.

---

### Post by tea for one on 2021-06-19
Your display is surprisingly unclaimed although Intel graphics drivers are built in to the kernel.
Probably, because you mentioned [highlight] I had to boot with nomodeset or 'safe graphics mode', otherwise it won't boot [/highlight]
I suspect that is why the driver has not loaded.

Here is my info using Intel graphics

```
edited@edited:~$ inxi -G
Graphics:
  Device-1: Intel Iris Plus Graphics 655 driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.9 driver: fbdev unloaded: modesetting,vesa 
  resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel Iris Plus Graphics 655 (CFL GT3) v: 4.6 Mesa 20.2.6 

```

Intel graphics are usually trouble-free and the driver is i915.

I did a quick internet search for[COLOR="#0000FF"] i915 not loading[/COLOR] and there were multiple answers for variations of similar problems.
It would be difficult to offer a suitable solution without sitting in front of your PC.

I suggest that you conduct your own search to see if anything is applicable or, alternatively, explore why your PC wouldn't boot the live session correctly.

---

