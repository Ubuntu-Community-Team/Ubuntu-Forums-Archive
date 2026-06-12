---
title: "New Ubuntu 20.04 Server and issue installing driver"
date: 2022-02-17
forum: General Help
---

### Post by shuhdonk on 2022-02-17
I have a new Ubuntu server vm running I am using for a plex server.  I am trying to install the Nvidia driver for my quadro P2000 and it will not let me sudo ./NVIDIA-Linux-x86_64-510.54.run to install it.  Typically you can press the tab key to finish the file name, that does not work either.  Gives me this error.

sudo: ./NVIDIA-Linux-x86_64-510.54.run: command not found


Ideas what is wrong?  thanks!

---

### Post by TheFu on 2022-02-18
VMs don't see the real hardware. They see a virtual GPU.
Which hypervisor is being used?  That can provide ideas for the best options to improve vGPU performance, but that is extremely hypervisor specific. I don't run my Jellyfin/Plex server in a VM. I don't use them to watch media either. I want the fastest access to storage for recording OTA TV.

---

### Post by shuhdonk on 2022-02-18
> **TheFu said:**
> VMs don't see the real hardware. They see a virtual GPU.
Which hypervisor is being used?  That can provide ideas for the best options to improve vGPU performance, but that is extremely hypervisor specific. I don't run my Jellyfin/Plex server in a VM. I don't use them to watch media either. I want the fastest access to storage for recording OTA TV.

Hey there, I have the card passed through, I am using Proxmox.  I figured it out though, I had to chown +X the nvidia driver download to be able to execute it (I am a linux newb).  It is all up and running perfectly now, including the quadro p2000.

---

### Post by TheFu on 2022-02-18
So you did all this, [https://pve.proxmox.com/wiki/Pci_passthrough](https://pve.proxmox.com/wiki/Pci_passthrough) , as a noob?
I have some doubts.  It is very possible that the GUI is working and performance is sufficient so you don't know that PCIe passthru isn't working.

---

### Post by shuhdonk on 2022-02-18
> **TheFu said:**
> So you did all this, [https://pve.proxmox.com/wiki/Pci_passthrough](https://pve.proxmox.com/wiki/Pci_passthrough) , as a noob?
I have some doubts.  It is very possible that the GUI is working and performance is sufficient so you don't know that PCIe passthru isn't working.

It is working, also setup Truenas scale as a VM and passed through my LSI HBA (IT mode) and have all 8 of my 16tb hdds setup as my network share.  Passed through another gpu as well (1050 TI) to a Windows 10 vm and that is also working properly with latest nvidia drivers installed etc.  Yes I am a newb but have done a lot of reading and tutorials on setting this all up.

---

### Post by TheFu on 2022-02-19
That is impressive for someone new.  You must have been very lucky with hardware choice, since only 2 of my systems over the decades has supported PCIe passthru and none have ever supported GPU passthru. Congratulations.

Very lucky indeed.

---

### Post by shuhdonk on 2022-02-19
> **TheFu said:**
> That is impressive for someone new.  You must have been very lucky with hardware choice, since only 2 of my systems over the decades has supported PCIe passthru and none have ever supported GPU passthru. Congratulations.

Very lucky indeed.

Hmm, I have a nvidia quadro p2000 passthru to plex vm, gtx 1050TI passthru to a win 10 VM, LSI HBA passthru to Truenas vm, I also have another hdd passthru to Truenas that is connected to my motherboards onboard slimsas port (can pass through each hdd individually (well maybe each port rather), has two slimsas ports on it, each port can have 8 sata drives).  A Supermicro H12SSL-NT motherboard.  I also have an intel 350t4v2 quad nic in the server and able to passthru each nic individually to vms.

[IMG]https://i.imgur.com/XojnFkD.jpeg[/IMG]

[IMG]https://i.imgur.com/q0bdoOp.jpeg[/IMG]

[IMG]https://i.imgur.com/saTB6uZ.jpeg[/IMG]

[IMG]https://i.imgur.com/ql5TT8o.jpeg[/IMG]

---

