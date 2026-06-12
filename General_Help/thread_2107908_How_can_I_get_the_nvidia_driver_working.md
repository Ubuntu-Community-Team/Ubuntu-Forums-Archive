---
title: "How can I get the nvidia driver working?"
date: 2013-01-23
forum: General Help
---

### Post by Steveire on 2013-01-23
Hi there,

I'm trying to get the drivers I need to use more recent opengl than mesa allows.

Here is my lspci:

```

$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [Quadro NVS 4200M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF119 HDMI Audio Controller (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
0b:00.0 SD Host controller: O2 Micro, Inc. Integrated MMC/SD controller (rev 05)
0b:00.1 Mass storage controller: O2 Micro, Inc. O2 Flash Memory Card (rev 05)

```

When I started (clean in terms of my attempts to get the graphics working), I was only getting a black screen when trying to show an example application which uses recent opengl.

So I tried installing the nvidia-current package. Now the example application just crashes, and when I run glxinfo I get this:

```

$ glxinfo
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

```

I also tried running the nvidia-xsettings executable, which creates a xorg.conf (my system otherwise does not have an xorg.conf, and I thought they were obsolete). When I restart X, my resolution is awful and unusable. So, I deleted the created xorg.conf.

Someone also pointed out [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee) to me. I have no idea if it is relevant to me. It says it's for NVIDIA Optimus.

So, the current state I have is that glxinfo crashes.

Can anyone help me to use modern opengl?

I use kubuntu, so any instructions through menus won't mean anything to me, but I can use a terminal.

Thanks,

Steve.

---

### Post by omeomi on 2013-01-23
Have you tried adding this repository for more recent Nvidia drivers?

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```

The Bumblebee software is only relevant for laptops, and from your specs I guess you use a desktop?

---

### Post by Steveire on 2013-01-23
I haven't tried those other packages.

This is a laptop.

---

### Post by omeomi on 2013-01-23
> **Steveire said:**
> This is a laptop.

In that case you might want to give Bumblebee a try. The combination of the Intel graphics and dedicated Nvidia card is not usually working very well without that.

---

### Post by Steveire on 2013-01-23
Ok, thanks I'll see if I can get bumblebee working. From the wiki page:

> 
Using Bumblebee, you can use your NVIDIA card for rendering graphics which will be displayed using the Intel card. 


Can't I just use the NVIDIA card for rendering and display? Can I just turn off the intel card or something?

---

### Post by omeomi on 2013-01-23
> **Steveire said:**
> Can't I just use the NVIDIA card for rendering and display? Can I just turn off the intel card or something?

Unfortunately not, the OS only has direct access to the Intel chip and indirectly to the Nvidia card. If you would turn off the Intel card the system would not be able to "reach" the Nvidia card.

I have been using Bumblebee in my laptop for a while now and it works pretty good for me.

---

### Post by Steveire on 2013-01-23
Yes, I've installed it now and it is able to run the examples I'm throwing at it. Thanks for your help!

It does seem to use 50% CPU though whenever I'm running one.

---

