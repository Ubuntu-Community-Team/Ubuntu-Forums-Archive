---
title: "Ubuntu 20.04 Focal Fossa Freezing on Virtual Box bootup"
date: 2022-07-06
forum: General Help
---

### Post by cafleck5 on 2022-07-06
[COLOR=#333333][FONT=&quot]Hey guys,[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]I am trying to run an Ubuntu 20.04 Focal Fossa Virtual Machine using Oracle's VirtualBox. It seems to be mostly running fine, but on occasion (a little over half the time) it freezes during startup and must be entirely restarted. This can occur any time while the system is booting up, or even right when it starts. I have noticed that if it boots and then freezes, the clock does still update, but I cannot see my mouse or use my keyboard at all. I currently have 4096 MB base memory, 4 virtual processors, and 20 GB for the virtual hard drive (which should be ample for running Ubuntu, I haven't even installed anything on it yet). I've tried the following unsuccessfully: toggling Enable PAE/NX, changing Paravirtualization Interface from Default to Minimal, and toggling Enable Nested Paging. I can't find any other advice online for resolving this, does anyone have any idea what would be causing this weird freezing issue? I'm relatively new to VirtualBox, so if there are any logs or data I can export that would help, let me know.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Thanks!![/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Charles[/FONT][/COLOR]

---

### Post by TheFu on 2022-07-07
Check the system logs.  Always start there. They are in /var/log/  There are many how-tos for this. Google "ubuntu log files", though logs are not ubuntu or even linux specific. All Unix-based systems have the same logs and searching them is the same.

> have 4096 MB base memory, 4 virtual processors, and 20 GB for the virtual hard drive
For a desktop, 4G RAM is fine, for a server, depending on workload, much less is usually needed.  

4 vCPUs is too many.  Start with 1. If that isn't sufficient, add 1 more. I've never needed more than 2 vCPUs.

20G is **not** sufficient for 22.04 desktop.  35G is the base minimal amount.  20.04 is really bloated since Canonical introduced snap packages and using a swap file instead of a swap partition/LV.
For a server, without any GUI programs, we can have a much smaller disk allocation, say 7G, but you'll need to be very careful that doesn't fill up.

I use VMs for almost everything.  Here's my main desktop, running 20.04, inside a VM:
```
$ inxi -bz
System:    Kernel: 5.4.0-121-generic x86_64 bits: 64 Desktop: FVWM 2.6.7
           Distro: Ubuntu 20.04.4 LTS (Focal Fossa) 
Machine:   Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996) 
           v: pc-i440fx-xenial serial: <filter> 
           Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: 1.10.2-1ubuntu1 
           date: 04/01/2014 
CPU:       2x Single Core (4-Die): AMD EPYC (with IBPB) type: MCM SMP speed: 3409 MHz 
Graphics:  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel 
           Display: server: X.Org 1.20.8 driver: none unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~60Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 256 bits) v: 4.5 Mesa 21.2.6 
Network:   Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge 
           driver: piix4_smbus 
           Device-2: Red Hat Virtio network driver: virtio-pci 
Drives:    Local Storage: total: 40.00 GiB used: 23.98 GiB (60.0%) 
Info:      Processes: 184 Uptime: 4d 19h 36m Memory: 3.84 GiB used: 1.30 GiB (33.7%) 
           Shell: bash inxi: 3.0.38 
```
I keep most data on network storage, so you can see that 24G is used.

As for RAM use:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:          3.8Gi       886Mi       579Mi       9.0Mi       2.4Gi       2.7Gi
Swap:         4.1Gi        13Mi       4.1Gi
```
Less than 1G is used, but I don't run any DE. If I did, about 1.5G of RAM would be used now.

I stopped using virtualbox around 2013. Started moving all my VMs do kvm+libvirt in 2010. I've never regretted that choice, but we all have different needs.

---

### Post by cafleck5 on 2022-07-11
Thanks for all of the advice!! I did bump up the core memory and down the number of processors, but it ended up being an issue with Hyper-v and VirtualBox competing. I disabled Hyper-v and everything seems to be working now!!

Thanks again!!
Charles

---

### Post by TheFu on 2022-07-11
> **cafleck5 said:**
> Thanks for all of the advice!! I did bump up the core memory and down the number of processors, but it ended up being an issue with Hyper-v and VirtualBox competing. I disabled Hyper-v and everything seems to be working now!!

Thanks again!!
Charles

Yes, for non-experts, only 1 hypervisor can be installed at the same time. Only 1 can be exclusively managing the VT-x or AMD-v extensions at a time.  It is possible to unload the kernel modules as needed on Linux VM hosts and load the 1 you want to use, but that's not something a typical user would do.


Thanks for reporting back.

The last thing I'd request is that you use the "Thread Tools" button near the top of the page and mark this thread as "SOLVED", so everyone can easily see that is the situation. This helps people looking for answers AND helps people wanting to help so they don't waste their time on already -solved- threads.

---

