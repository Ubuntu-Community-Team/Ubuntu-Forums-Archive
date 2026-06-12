---
title: "nvidia-installer-cleanup problem"
date: 2013-12-24
forum: General Help
---

### Post by cylent on 2013-12-24
Trying to perform the following:

 install bumblebee bumblebee-nvidia primus linux-headers-generic 


For some reason and this is totally odd i keep getting the following error:

E: /var/cache/apt/archives/_20130816+1+bsos12_amd64.deb: trying to overwrite '/usr/lib/nvidia/pre-install', which is also in package ubuntu-drivers-common 1:0.2.83

this is the error from Synaptic Package Manager.

please help!

[ATTACH=CONFIG]248863[/ATTACH]

---

### Post by efflandt on 2013-12-26
Which Ubuntu version and are you trying to do all those before installing nvidia drivers?

In 64-bit 13.10 I think all I had to do was install the nvidia drivers. Not sure which version is best, but I installed **nvidia-experimental-310** (which is actually currently 319.60), although, I forget if I used Software Center or Synaptic. In any case bumblebee-nvidia and primus were automatically installed at that point, because when I tried to install them with apt-get it said they were already the newest versions.

Although, to run steam and steam games I had to add some 32-bit libs, add /etc/ld.so.conf.d/steam.conf to point steam to 32-bit libs, and figure out additional command line parameters to launch steam games with **optirun** (I just used Intel graphics for steam itself). Intel HD 4600/Nvidia GTX 765M

---

