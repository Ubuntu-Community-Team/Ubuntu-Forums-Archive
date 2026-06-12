---
title: "Screen blank after suspend/login - Nvidia/Intel GPUs, Asus Zenbook, Peppermint"
date: 2019-12-02
forum: General Help
---

### Post by the_mulletator on 2019-12-02
2 Issues with suspend/login

Issue #1: 
Screen going blank after suspend/login.  I can see the login screen but after logging in the screen is blank.

The issue seems to occur only after returning from suspend after the laptop lid has been closed for a while (more than a few minutes).  It doesn&#8217;t occur only from suspend or after being suspended for a few minutes.  It must be suspended for longer.  

When the screen is blank I can access the terminal via ALT + F2 but haven't been able to rescue the X session. I have either restart the X server or reboot the machine. Both are extremely annoying.

I have the proprietary Nvidia drivers (details below) I have tried setting the Intel GPU using the Nvidia Prime settings the problem occurs with both Nvidia and Intel GPUs.

I'm not sure what exactly is causing the problem or how to fix it. I also don't know how to save the X session without having to close everything. If I could do that it wouldn't be so bad.


Issue #2:

If I lock the screen (CTRL + ALT + L) and then close the lid I lose my session.  It seems like I get logged out.  When I log in again everything is gone (browser tabs, open programs, etc).  If I only lock the screen and log in again everything is OK.  Something happens when I close the lid.

The two issues are possibly related.

I have some settings to help inprove battery life.  As suggested in this articel ([https://medium.com/@tomwwright/better-battery-life-on-ubuntu-17-10-4588b7f72def]("https://medium.com/@tomwwright/better-battery-life-on-ubuntu-17-10-4588b7f72def")).

These are the steps:
```
sudo apt-get update
sudo apt-get install tlp tlp-rdw powertop
sudo tlp start
sudo powertop --auto-tune

```

I'm not sure if that's related or what TLP actually does.

I can provide more info if necessary.
Please help. 


Here's some details on my setup:
laptop: Asus Zenbook 15 (UX533FD-DH74)
OS: Peppermint 10
GPUS: GTX 1050 Max-Q, Integrated Intel
Dual boot with Win10



```
ASUS ~ $ sudo lshw -C display 
``````

 *-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:147 memory:b2000000-b2ffffff memory:90000000-9fffffff ioport:4000(size=64) memory:c0000-dffff
  *-display UNCLAIMED
       description: 3D controller
       product: GP107M [GeForce GTX 1050 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b3000000-b3ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:3000(size=128) memory:b4000000-b407ffff

```

```

ASUS ~ $ nvidia-smi
Mon Dec  2 18:15:03 2019       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.116                Driver Version: 390.116                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 105...  Off  | 00000000:02:00.0 Off |                  N/A |
| N/A   51C    P5    N/A /  N/A |    483MiB /  2002MiB |      2%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0      1089      G   /usr/lib/xorg/Xorg                           238MiB |
|    0      1882      G   ...equest-channel-token=634626956115621631   244MiB |
+-----------------------------------------------------------------------------+

```

```
ASUS ~ $ sudo cat /etc/X11/default-display-manager
/usr/sbin/lightdm

```

```
ASUS ~ $ cat /etc/systemd/logind.conf
#  This file is part of systemd.
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See logind.conf(5) for details.


[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
#InhibitDelayMaxSec=5
#HandlePowerKey=poweroff
#HandleSuspendKey=suspend
#HandleHibernateKey=hibernate
#HandleLidSwitch=suspend
#HandleLidSwitchDocked=ignore
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#HoldoffTimeoutSec=30s
#IdleAction=ignore
#IdleActionSec=30min
#RuntimeDirectorySize=10%
#RemoveIPC=yes
#InhibitorsMax=8192
#SessionsMax=8192
#UserTasksMax=33%

```

---

### Post by wildmanne39 on 2019-12-02
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by the_mulletator on 2019-12-04
Does anyone have any advice at all?

---

### Post by the_mulletator on 2019-12-04
Does anyone have any advice at all?  This is a really annoying problem and is getting in the way of my work.

---

