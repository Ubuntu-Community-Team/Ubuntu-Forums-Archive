---
title: "Dual monitor config issues on latest 12.04 updates??"
date: 2012-10-22
forum: General Help
---

### Post by roboavatar on 2012-10-22
I am a relatively new user of Ubuntu and I am using 12.04 LTS. Today I discovered  when my system boots it enters into one of my user accounts automatically (I have them setup for my children). My system has dual monitors and only one monitor is receiving a video signal. The resolution is incorrect. Any windows that are open are split on the screen and I cant get focus of them. Also I cant open a a terminal with the <ctl><alt> <T> key strokes.  

I cant log out of this user account but I can log into my administrator account. In this case the dual monitors do behave correctly and are configured for the proper resolution. 

I believe this issue came out of my last upgrade on 12.04 (I usually try to keep up with the latest upgrades). But I cant be certain. 

Is there any known dual monitor issues that came with the last set of recent updates.  How else could I determine any update issues rather than posting on a general forum. 

Your help is very much appreciated.

---

### Post by ~LoKe on 2012-10-22
Which video card & driver?

---

### Post by roboavatar on 2012-10-23
My card is 

lspci -nn | grep VGA

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF114 [GeForce GTX 560] [10de:1201] (rev a1)


My driver is 

~$ jockey-text -l 
kmod:nvidia_experimental_310 - Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library (Free, Disabled, Not in use)
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_current_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Enabled, In use)
xorg:nvidia_experimental_304 - NVIDIA accelerated graphics driver (**experimental** beta) (Proprietary, Disabled, Not in use)



Is there anyway I can revert to a previous driver to test this out? Where could I find this information?

---

### Post by roboavatar on 2012-10-23
~$ sudo  lshw -c video 
  *-display               
       description: VGA compatible controller
       product: GF114 [GeForce GTX 560]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f6000000-f7ffffff memory:e0000000-e7ffffff memory:ec000000-efffffff ioport:af00(size=128) memory:e8000000-e807ffff
  *-display
       description: Display controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:48 memory:fb400000-fb7fffff memory:d0000000-dfffffff ioport:ff00(size=64)

---

