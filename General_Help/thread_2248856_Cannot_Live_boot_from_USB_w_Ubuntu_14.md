---
title: "Cannot Live boot from USB w/ Ubuntu 14"
date: 2014-10-17
forum: General Help
---

### Post by Donald_Smith on 2014-10-17
Hello,

I'm trying to make use of an Ubuntu live USB, but here's my problem: it's worked before with no major configuration changes on the host system.
My hosting system is a Windows 7 64x. The only real oddity is a Nvidia 660Ti.

Anyhow, I've used the same USB before and never had any issues booting with it, but now I consistently get any combination of issues:
1. Black screen with blinking cursor
2. Black screen with white chunk full of ^U characters
3. Purple loading screen hangs

The only thing I've changed on the host system that I can think might be having some sort of effect on this was I'm using a VM with VMplayer to access another Ubuntu distro for my compsci courses. The issue is I can't virtualize this one because I specifically want the information to be segregated from a host OS.

Anyhow, I've used most of the major tools I've seen mentioned to try fixing this issue and I've re-torrented the Ubuntu LTS 14.04 64x version some 5 times now (from the source, ofc). I've tried Universal USB Installer (the linux one mentioned in Canonical's help documentation) the Ubuntu live USB creator (using my VM) ISO to USB, and Unetboot, all with the same end results.

Any assistance is much appreciated.

---

### Post by sudodus on 2014-10-20
Welcome to the Ubuntu Forums :-)

I suspect your 'only real oddity': Nvidia graphics may need a boot option, start trying with **nomodeset**.

See this link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

And when it has booted, try to install a proprietary graphics driver (an nvidia driver).

-o-

There may be problems with your iso file (but it is less likely than than problems with the graphics). Instead of repeated downloads (or torrenting) you can check the ***md5sum***. 

See this link [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

and there may be problems with the tool installing into the pendrive or the pendrive itself (also less likely but possible).

See this link [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

