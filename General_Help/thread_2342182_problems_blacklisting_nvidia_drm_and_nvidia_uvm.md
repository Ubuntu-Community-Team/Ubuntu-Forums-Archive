---
title: "problems blacklisting nvidia_drm and nvidia_uvm"
date: 2016-11-04
forum: General Help
---

### Post by davidv1992 on 2016-11-04
I have a laptop with an nvidia optimus setup (asus N751JK) running xubuntu 14.04.5

The way i currently have bumblebee setup requires me to block the nvidia drivers from loading during boot using blacklists, otherwise it will try to use that card as primary video card (which wont work, because it has no output port physically connected to it) and give a black screen. This was working fine until a recent update installed the nvidia drivers version 367, specifically the packages libcuda1-367, nvidia-367, nvidia-opencl-icd-367.

With these packages for some reason the modules nvidia_drm and nvidia_uvm will always load during boot. I have tried to disable this by adding "blacklist nvidia_drm" and "blacklist nvidia_uvm" to both /etc/modprobe.d/bumblebee.conf and /etc/modprobe.d/blacklist.conf. Neither location however seemed to have any influence, the modules are still loaded. I have verified that nothing depends on them (lsmod lists no modules under used_by), and ran update-initramfs -u after any changes.

Next up tried a more aggresive method of disabling the modules, by adding "install nvidia_drm /bin/false" to the aformentioned files, again running update-initramfs -u and trying again. Even this did not disable the modules, and I'm pretty much out of ideas on how to disable these modules. Does anybody have any suggestions as to how to disable them?

---

### Post by davidv1992 on 2016-11-06
Solved it after diving into the files actually provided by the package.

blacklisting nvidia-367-drm, nvidia-367 and blocking the nvidia persistence daemon  was enough, on to the next issues

---

