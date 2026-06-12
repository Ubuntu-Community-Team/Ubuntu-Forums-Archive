---
title: "Problem getting better than 800x600 screen resolution"
date: 2016-10-30
forum: General Help
---

### Post by Neill_R on 2016-10-30
Hi
    I am trying to get better than 800 x 600 screen resolution.

My system is an Intel server board S3420G and a Proview CY 765 model 780 flat screen panel monitor.

Ubuntu Server 16.04.1 has been installed and to that lubuntu-desktop added via synaptic.

If I run a LiveCD of Lubuntu 16.04.1 I get 1024 x 768. So the hardware is capable of better than 800 x 600 

lspci -nn | grep VGA
03:00.0 VGA compatible controller [0300]: Matrox Electronics Systems Ltd. MGA G200e [Pilot] ServerEngines (SEP1) [102b:0522] (rev 02)
neill@Xeon-Ubuntu-Server:~$ grep -i 102b0522 /usr/share/xserver-xorg/pci/*.ids
grep: /usr/share/xserver-xorg/pci/*.ids: No such file or directory



Going to check with LiveCD as driver "mga" is not loaded

```

neill@Xeon-Ubuntu-Server:~$ sudo lshw -c video
[sudo] password for neill: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: MGA G200e [Pilot] ServerEngines (SEP1)
       vendor: Matrox Electronics Systems Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b0000000-b0ffffff memory:b1800000-b1803fff memory:b1000000-b17fffff memory:b1810000-b181ffff
neill@Xeon-Ubuntu-Server:~$ sudo modinfo
modinfo: ERROR: missing module or filename.
neill@Xeon-Ubuntu-Server:~$ sudo modinfo mga
filename:       /lib/modules/4.4.0-45-generic/kernel/drivers/gpu/drm/mga/mga.ko
license:        GPL and additional rights
description:    Matrox G200/G400
author:         Gareth Hughes, VA Linux Systems Inc.
firmware:       matrox/g400_warp.fw
firmware:       matrox/g200_warp.fw
srcversion:     DBE698C025A9D748E452CD1
depends:        drm
intree:         Y
vermagic:       4.4.0-45-generic SMP mod_unload modversions 
neill@Xeon-Ubuntu-Server:~$ 


```

---

### Post by daftykins on 2016-10-30
Hi

Ah Matrox, a true museum piece. If you run the following we can see which graphics driver is in use when you start up:

sudo apt install pastebinit && pastebinit /var/log/Xorg.0.log

Then link us to the URL provided.

---

### Post by Neill_R on 2016-11-03
I have foudefauklnd a work around by setting the resolution to 1024x768 in grub. 

```
/etc/default/grub
GRUB_GFXMODE=1024x768
```

URL = [http://paste.ubuntu.com/23423157](http://paste.ubuntu.com/23423157)

Here is the I see the "mga" module is missing? Looking into installing the mga module(driver) this looks complicated and outside my experience level

I have a XEON process on an Intel server motherboard S3420GP (Tempus Birmingham UK built now defunct) 
which driver to pick  [http://www.matrox.com/graphics/en/support/drivers/previous/display/](http://www.matrox.com/graphics/en/support/drivers/previous/display/) this might be a problem

---

### Post by Neill_R on 2016-11-06
Solved

I had not ever before need to install a driver.
Having had my system crash into low graphics mode I wiped the whole system and started again
```

installed Ubuntu 16.04.1 Ubuntu server
sudo apt-get install lubuntu-desktop
then in synaptic installed xserver-xorg-video-mga and xserver-xorg-video0mga-lts-xenial

```

---

