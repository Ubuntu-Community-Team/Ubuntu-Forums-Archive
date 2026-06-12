---
title: "Find non-Mesa proprietary drivers for Intel Iris Xe"
date: 2024-03-07
forum: General Help
---

### Post by lubaskinc0de on 2024-03-07
Hello, I recently had a problem - intentionally hangs the system when playing WarThunder - just at random moment everything hangs, no combinations (ctrl + alt + t, ctrl + alt + f7) do not work At such a moment only to turn off the computer with a physical button. I looked at the supposed dmesg log during the hang - everything leads to the graphics driver (I have an Intel Iris Xe video card). But this has never happened in other programs. I wrote to the bug tracker of the game - and I was told that Mesa drivers are not supported and I need proprietary drivers.What did he mean and where can I get these proprietary drivers for Intel Iris Xe?

Ubuntu 22.04.4 LTS with GNOME


The dmesg and inxi -F logs are attached.

[ATTACH]293464[/ATTACH]
[ATTACH]293465[/ATTACH]

---

### Post by monkeybrain20122 on 2024-03-08
Check if it applies [https://dgpu-docs.intel.com/driver/installation.html#ubuntu-install-steps](https://dgpu-docs.intel.com/driver/installation.html#ubuntu-install-steps)

---

### Post by MAFoElffen on 2024-03-10
@et-all ---

Wait. [COLOR=#ff0000]Do not do that...[/COLOR] If you want to go that way (Intel OOT for Ubuntu 22.04), then join me in my efforts to get the upstream Intel Graphics Support Team to get those drivers working for 22.04 with 6.5 kernels.

I've been working with two upstream Intel Support Graphics Engineer Teams since it started failing at 6.2.X Series kernels since September. We got that working (except for ZFS-On-Root machines)... Now they are working to get it working for 6.5.x series kernels. 

They are not there yet. That is not ready yet.

If you want to help getting those working for Ubuntu, contact me and I will give you instructions. That may get them know that they might need to shift more resources to get those working(?) I have a Bug Reported at LaunchPad, and an open Intel Support Case. They only are supposed to work with specific Intel GPU's...

---

### Post by monkeybrain20122 on 2024-03-10
> **MAFoElffen said:**
> @et-all ---

Wait. [COLOR=#ff0000]Do not do that...[/COLOR] If you want to go that way (Intel OOT for Ubuntu 22.04), then join me in my efforts to get the upstream Intel Graphics Support Team to get those drivers working for 22.04 with 6.5 kernels.

I've been working with two upstream Intel Support Graphics Engineer Teams since it started failing at 6.2.X Series kernels since September. We got that working (except for ZFS-On-Root machines)... Now they are working to get it working for 6.5.x series kernels. 

They are not there yet. That is not ready yet.

If you want to help getting those working for Ubuntu, contact me and I will give you instructions. That may get them know that they might need to shift more resources to get those working(?) I have a Bug Reported at LaunchPad, and an open Intel Support Case. They only are supposed to work with specific Intel GPU's...

Hi, I have no idea about it since I don't have xe, but for OP's benefit I found your bug reports and link them here, maybe that will give him and those who run into similar problems and found this thread a better idea about the issue.

[https://community.intel.com/t5/Graphics/Ubuntu-intel-i915-kdms-error-on-update/td-p/1524576?profile.language=en](https://community.intel.com/t5/Graphics/Ubuntu-intel-i915-kdms-error-on-update/td-p/1524576?profile.language=en)

[https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/2036452](https://bugs.launchpad.net/ubuntu/+source/glibc/+bug/2036452)

---

