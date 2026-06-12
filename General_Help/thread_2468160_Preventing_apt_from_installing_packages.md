---
title: "Preventing apt from installing packages"
date: 2021-10-20
forum: General Help
---

### Post by raskallen on 2021-10-20
Hi

We have a HPC vmware cluster with vGPU support for virtual machines. The vm-s require a special, licensed driver to use the vGPU. The only way I can install these drivers is with NVIDIAs own installer. It works great. When I provision a vm, it comes with NVIDIA drivers and Cuda toolkit preinstalled. Machines run Ubuntu 20.04, server or desktop version depending on the users needs.

However, when users get their playground vm, they don't bother to check if the driver and the CUDA toolkit is installed, even when I inform them, and the first thing they do is to install NVIDIA drivers and CUDA from apt. This breaks the vms connection to the GPU cards. 

I want to block users from installing anything *nvidia*. I have tried the following:

1. apt-mark hold *nvidia*    - This blocks packages as wanted, confirmed with 'apt-mark showhold', but when I check again after some time, the list of held packages is empty. What am I missing? Can I only hold already installed packages?
2. Pinning the packages with an entry in /etc/apt/preferences.d. Doesn't work
3. echo "nvidia-driver-470 hold" | dpkg --set-selections - I guess this would work, but it doesn't accept wildcards, so I must run a command for each package and keep checking the repo if there are new packages that can break things. I don't want to do this.

What am I doing wrong? How can I prevent the users from breaking there systems? I have considered removing sudo access, but that will give me more work than reinstalling from nvidia-installer when they break things.

---

### Post by vanadium on 2021-10-20
Pinning should do it. Provide detail on how you attempted this.

---

