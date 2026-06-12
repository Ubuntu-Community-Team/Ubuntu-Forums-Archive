---
title: "Installation two OS on one server"
date: 2022-09-28
forum: General Help
---

### Post by ODBWilson on 2022-09-28
Just wondering which software will be the best for server virtualization for free.
I want to install two Ubuntu server on one physical server: one is LIVE server; another one is backup server.
Can someone shed some light on it?
I am not familiar with Linux virtualization.
Any proposed solution from the web?

Thanks,
Wilson

---

### Post by HermanAB on 2022-09-28
Gnome Boxes will make it easier for you to experiment.  However, I prefer Oracle Virtualbox.

---

### Post by oldfred on 2022-09-28
Search forum for TheFu and posts on virtual installs. Change to most recent first. Paste this into Google.
site:ubuntuforums.org TheFu virtualization

 Some comments from TheFu, I saved as thinking about virtual install myself.
He uses KVM with the libvirt and virt-manager addon packages.
I ran 15 VMs on a Core2 Duo system in 2010. One of those was Win7 Ultimate with all the bloat that includes.
[https://ubuntuforums.org/showthread.php?t=2468309&page=2](https://ubuntuforums.org/showthread.php?t=2468309&page=2)

Today a Ryzen 2600 (13K passmarks) on VM host, which is about the same speed as the 1700x (15.5k passmarks) and easily runs 20 VMs and 4 linux containers. It uses a little over 16G of RAM, but that can easily be controlled by limiting the concurrent VMs running and not over allocating limited resources to VMs. In general, I give a Linux VM, 1vCPU and 1GB of RAM, unless I 100% KNOW is needs more. My normal desktop runs inside a VM an get 3G of RAM with 1 vCPU. A Windows VM gets 3GB of RAM and 2 vCPUs, but it is powered off almost all the time.

Duckhook - Containers Sandboxing Desktop Apps With LXD
[https://ubuntuforums.org/showthread.php?t=2438709](https://ubuntuforums.org/showthread.php?t=2438709)

From TheFu  
[https://ubuntuforums.org/showthread.php?t=2459660&page=2](https://ubuntuforums.org/showthread.php?t=2459660&page=2)
But, there are a number of hypervisors that run well on Ubuntu and are stable and fast. There are desktop-centric hypervisors and enterprise versions.

---

### Post by ODBWilson on 2022-09-29
Thank You all.  I will take a look!

---

### Post by HermanAB on 2022-09-29
Gnome Boxes is probably the easiest way to use QEMU, KVM and libvirt.

---

### Post by ODBWilson on 2023-08-29
Finally, I use KVM with the libvirt and virt-manager.  It has been running smoothly.
Just wondering if I wanna setup the 2-node cluster for the active-passive configuration on these VMs.
Any recommended software?  

Thanks in advance.

---

### Post by jsdata on 2023-08-29
I run my 'LIVE' installation on my laptop and a 'backup server' running on a virtual (Windows Hyper-V). I'm not a fan of dual boot solutions on my computers.

---

### Post by ODBWilson on 2023-08-29
Any Linux cluster solution recommended?  I like to build on VMs (Primary and Backup) that I've already used.

---

