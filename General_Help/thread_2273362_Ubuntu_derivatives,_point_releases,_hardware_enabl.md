---
title: "Ubuntu derivatives, point releases, hardware enablement stack, and support periods"
date: 2015-04-12
forum: General Help
---

### Post by Keith_Helms on 2015-04-12
I've been using Ubuntu and Xubuntu for years and thought I knew how the process worked.   New LTS release every 2 years, LTS supported for 3 or 5 years, point release every now and then containing the current updated versions of software for the release.

I never stumbled across the HWE stack concept until I noticed that my Ubuntu 14.04.2 install had the 3.16 kernel and my Xubuntu 14.04.2 install had the 3.13 kernel.  Now I read that the point releases actually have shorter support schedules and I've become confused about multiple things.

1. Does the HWE stack concept only apply to the "official" Ubuntu version?  Why did my Xubuntu 14.04.2 install not come with the 3.16 kernel?

2. Does that imply that the 3.16 kernel is untested with the rest of the Xubuntu 14.04 software and it's more risky to use than on Ubuntu 14.04 where it supposedly has been tested?

3. Support period.  If you've never used Linux in your life and you go to download Ubuntu, by default you are shown the 14.04.2 version with the following text

> 
Ubuntu 14.04.2 LTS

The Long Term Support (LTS) version of the Ubuntu operating system for desktop PCs and laptops, Ubuntu 14.04.2 LTS comes with five years of security and maintenance updates, guaranteed.


Yet, 14.04.2 comes with the 3.16 kernel and according to the documentation that is only supported for 18 months.  A new user who just lets software updater handle things would have to manually trigger an update to a newer kernel at that point or fall into the non-supported category.   Isn't that kind of fibbing about the support period?

4. If I manually install the HWE stack, does the current kernel series continue to update?  For example, if I'm on 3.13.0-49, will I get the update to 3.13.0-50 when it comes out, or will I only get updates to 3.16 at that point?

---

### Post by CantankRus on 2015-04-12
I too am intersested in this.
Surely the iso download offered would be the one with longest support? 
I was under the same impression as Keith_Helms and recently used [**_[COLOR="#B22222"]THIS[/COLOR]_**]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") page for the LTS enablement stacks because I read the point release had a later kernel.

I just used [**_[COLOR="#B22222"]THIS[/COLOR]_**]("https://wiki.ubuntu.com/1204_HWE_EOL#Tool") guide to install **hwe-support-status**

```
**[COLOR="#008000"]glen@Trusty:~/hwe-support-status$[/COLOR] ./hwe-support-status --verbose**
Your Hardware Enablement Stack (HWE) is supported until April 2017.
```
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] inxi -b**
System:    Host: Trusty Kernel: 3.16.0-33-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 version: x.x Bios: Award version: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) clocked at 1800.00 MHz 
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti] 
           X.Org: 1.16.0 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1680x1050@59.9hz 
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.4.0 NVIDIA 331.113
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1250.3GB (13.2% used)
```

---

