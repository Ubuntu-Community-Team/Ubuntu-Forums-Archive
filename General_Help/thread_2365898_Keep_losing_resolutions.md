---
title: "Keep losing resolutions"
date: 2017-07-11
forum: General Help
---

### Post by jacatone on 2017-07-11
Been installing Lubuntu 16.10 on some old Win XP and Vista machines. Everything works fine after the installs but then the resolution drops from the correct 1920x1080 down to 1024x768 and I can't figure out why. They all have separate Nvidia AGP cards which worked fine in Windows. Tried the driver search feature but that came up empty. Anyone have a solution?

---

### Post by TheFu on 2017-07-12
Support for 16.10 ends in - like - 2 weeks.  17.04 support is 9 months from the release too.

16.04 is really the version you should be installing. That will be supported until 2021. **<--- is incorrect see posts below for correct Lubuntu support dates.**

There isn't some secret to support dates. They are published and follow a known pattern.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by vasa1 on 2017-07-14
Lubuntu LTS has support only for three years and that applies to Lubuntu 16.04 LTS as well. I don't know whether a Lubuntu 16.04 LTS user will continue getting support for the aspects of the system that are common to Lubuntu LTS and to Ubuntu LTS (which has support for five years).

---

### Post by again? on 2017-07-14
Installing inxi (sysinfo script) and posting the output would help.
```
sudo apt install inxi
```
```
inxi -b
```
eg
```
glen@GU17:~$ inxi -b
System:    Host: GU17 Kernel: 4.10.0-26-generic x86_64 (64 bit) Desktop: Gnome 3.24.2 Distro: Ubuntu 17.04
Machine:   Device: desktop Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x BIOS: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1400/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.19.3 drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.88hz
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 375.66
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
Drives:    HDD Total Size: 870.2GB (13.7% used)
Info:      Processes: 279 Uptime: 2 days Memory: 1605.8/3931.5MB Client: Shell (bash) inxi: 2.3.8
```

---

### Post by Bucky Ball on 2017-07-14
As in previous posts, forget 16.10. Almost dead. Lubuntu 16.04 LTS has support until 2019 April so best to get on that train unless you fancy upgrading to a new release every six or so months. No sooner will you have 16.10 installed than you'll need to upgrade to 17.04, so save yourself some time and effort. ;)

(* Further note: LTS releases can be upgraded via the net to the next LTS version. For example, 16.04 LTS will be upgradeable to 18.04 LTS when it's released in 2018, leapfrogging the interim releases in between. 

Interim releases, supported for nine months, can only upgrade via the net to the next release, 16.10> 17.04> 17.10> 18.04 LTS. Food for thought.)

---

### Post by jacatone on 2017-07-26
Still doesn't explain why my resolution keeps degrading. Maybe I should ask what version I should use? Them I might get my question answered.

---

### Post by BenginM on 2017-07-26
Salutations! is this happening with bult-in screen or an external monitor?  I presume this is while using the free driver Nouveau .. when you said "Tried the driver search feature but that came up empty" you mean using the Additional driver section to install the Nvidia driver , Right!

 #see
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Bucky Ball on 2017-07-26
> **jacatone said:**
> Maybe I should ask what version I should use? Them I might get my question answered.

Using a supported Lubuntu release might help get your question answered. That would be Lubuntu 16.04 LTS or 17.04. Good luck. ;)

A quick look [found this]("https://forums.geforce.com/default/topic/982108/geforce-drivers/gtx-1050-ti-bad-resolution-in-ubuntu-16-04-nvidia-375-26-/post/5175620/#5175620") which refers to your card and 16.04. You could try updating/upgrading the 16.10 you have, which may upgrade your kernel, and see if that makes any diff.

```
sudo apt update
sudo apt full-upgrade
```

The last command will NOT upgrade your release to a newer one. As 16.10 is a dead release you may not get much joy from the update/upgrade.

---

### Post by QIII on 2017-07-26
The reason you are getting the advice to use a supported release is that issues with unsupported releases may be difficult or impossible to resolve.

More important, however, is that we as a community ask people to keep their releases up to date so that users avoid the pitfalls and security issues associated with EOL releases.

The purpose is not to avoid your question, but to provide prudent and helpful support.

---

### Post by Yellow Pasque on 2017-07-27
When it boots in 1024x768, give us the /var/log/Xorg.0.log file so maybe we can figure out why. Use code tags as it's a lot of text.

---

