---
title: "LG 4k TV Only Has 760P Resolution Option on Ubuntu 22.04.4 with GeForce GTX 1660 SUPE"
date: 2024-03-08
forum: General Help
---

### Post by Gnewbie on 2024-03-08
I connected my Ubuntu 22.04.4 box to a 50" 4k monitor.  I was originally able to select the 4k resolution from the drop down, but intermittently it would only display 760p with not option in settings to change it.  A restart or two fixed it in the past, but the 760p is persistent today.
My video card is GeForce GTX 1660 SUPER.

Can anyone help me troubleshoot? I've been at it for an hour or two and gotten nowhere.

TIA...

---

### Post by Gnewbie on 2024-03-08
My NVIDIA driver is not being recognized.

```
$ cat /proc/driver/nvidia/version
cat: /proc/driver/nvidia/version: No such file or directory
```

I get an error when I try to install drivers.  I started with 545, got errors, went to 525 and got the following error:

```
$ sudo ubuntu-drivers install nvidia:525
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libnvidia-extra-525 : Conflicts: libnvidia-extra
 libnvidia-extra-535 : Conflicts: libnvidia-extra
 nvidia-kernel-common-525 : Conflicts: nvidia-kernel-common
 nvidia-kernel-common-535 : Conflicts: nvidia-kernel-common
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by #&amp;thj^% on 2024-03-08
It's best to start fresh with nVidia Drivers:
1st. remove all failed drivers:
```
sudo apt autoremove --purge nvidia*
```

---

