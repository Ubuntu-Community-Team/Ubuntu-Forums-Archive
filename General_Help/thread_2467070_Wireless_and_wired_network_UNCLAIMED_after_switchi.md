---
title: "Wireless and wired network UNCLAIMED after switching to open source display driver"
date: 2021-09-15
forum: General Help
---

### Post by lava2 on 2021-09-15
Long story short, I switched from NVIDIA 470 proprietary driver to the X.Org open source display driver on my Dell G3 running 20.04. Rebooted and all of a sudden I have zero internet connectivity. Which means I can't reinstall the proprietary driver. 

Doing a sudo lshw -C networks shows that both the wireless and wired network conrollers are "UNCLAIMED". 

How can I fix this if I don't have an internet connection - Download the proprietary driver onto a USB stick?

---

### Post by lava2 on 2021-09-15
Ok, DL'd the proprietary driver to a USB stick, attempted to install it. Got an error that I needed 'cc' in my path since I didn't have gcc/built-essentials. Put that on the USB and has errors installing that due to unmet dependencies. Looks like I need to buy a USB wireless adapter. This sucks.

---

### Post by ActionParsnip on 2021-09-15
What is the output of:
```

sudo lshw -C network

```

---

### Post by grahammechanical on 2021-09-15
How did you do this "switch" from the Nvidia driver? When we use Software & Updates>Additional Drivers tab to switch between proprietary and open source video drivers it does not usually result in the Ethernet and WiFi drivers being removed also. On my system Ethernet and WiFI have different drivers anyway. This may not be the case with your system.

Is it possible that a setting in the BIOS/UEFI has disabled the Ethernet and WiFi adapters? Check to see if the BIOS/UEFI is recognising the existence of Ethernet and WiFi adapters.

Another thing to try is to load a recovery mode kernel and use the recovery menu. At the Grub boot menu select Advanced Options for Ubuntu and then select a Linux kernel with recovery mode. At the recovery menu select Network, That will set up an internet connection using the settings already put into the system.

If that fails to establish an internet connection and you are confident that there is an actual connection between the router/hub and the Internet Service Provider, then it may well be that the drivers for both Ethernet and WiFi have been removed.

Regards

---

### Post by lava2 on 2021-09-15
I did the switch using the Additional Drivers tab. This is something  I've done before with different machines and never experienced this  issue, I have no idea why it killed networking. Bluetooth doesn't work  either.

All networking is enabled in the BIOS. 

I went  into recovery mode one kernel back, turned on networking, and everything  came up fine and I could connect to wireless. So the hardware is ok. I  went ahead and reinstalled the proprietary driver, and discovered I  already had build-essential installed. However, when I reboot into the  latest kernel not in recovery mode, networking is still disabled. How  can I enable it? I tried everything on this page, but nothing worked:
[https://askubuntu.com/questions/207020/command-for-enabling-networking](https://askubuntu.com/questions/207020/command-for-enabling-networking)

When I tried the *sudo service networking start* command, I got an error stating: command not found

Just  yesterday the latest kernel worked fine with my network hardware, I  have not updated the kernel recently, so I don't believe this is a  kernel incompatibility issue.

---

### Post by lava2 on 2021-09-15
> **ActionParsnip said:**
> What is the output of:
```

sudo lshw -C network

```

```
*-network UNCLAIMED       
       description: Network controller
       product: Wireless-AC 9560 [Jefferson Peak]
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
       resources: memory:a43a4000-a43a7fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:a4204000-a4204fff memory:a4200000-a4203fff

```

---

### Post by deadflowr on 2021-09-15
Look at the logs to see what else was removed during the purging.
At least for Ubuntu package management look in /var/log/apt, there are two files, history.log and term.log.
Look at history.log as it lists what is what and when it was done. The term.log breaks down the how it was done.

Also, which driver? The NVIDIA drivers built for Ubuntu or the driver from NVIDIA directly?
Were these the drivers from Ubuntu or somewhere else, I guess is what I'm asking.

---

