---
title: "Ubuntu 7.04 + VMware Tools: Shutdown Hangs"
date: 2007-07-15
forum: General Help
---

### Post by naijireja on 2007-07-15
Hi all,

I am currently running Ubuntu 7.04 as a guest in VMware Server 1.0.3.  The host OS is Windows XP Service Pack 2.  I have been able to install the version of VMware tools that came with VMware server, together with the vmhgfs patch found on this page:

[http://tuxx-home.at/archives/2007/06/29/T12_33_53/](http://tuxx-home.at/archives/2007/06/29/T12_33_53/)

In addition, I have installed the following packages:
vmware-tools-kernel-modules
vmware-tools-kernel-modules-2.6.20-15
vmware-tools-kernel-modules-2.6.20-16
xserver-xorg-video-vmware

The problem that I am having now is that the virtual machine hangs every time I try to shut it down or reboot.  I have to go into the VMware server console manually to turn off or restart the virtual machine after Ubuntu finishes shutting down.  This is problematic, because I need to be able to reboot the virtual machine remotely and still log back into it after rebooting is completed.

Has anyone else run into this issue?

Thanks,
--naijireja

---

### Post by TheExplorer on 2007-07-15
Use [Virtualbox]("http://virtualbox.org/"). No problems for me.

---

### Post by naijireja on 2007-07-15
I'll give that a shot, and I've always liked the idea of having an open-source hypervisor available (although since I'm on a Win32 host, and don't have the necessary dev tools for building VirtualBox on Windows, I'll just use their non-free personal edition).

In the meantime, I'll see how far I get in uninstalling the VMware tools from my Ubuntu guest, since I usually just remote into the VM anyway and don't strictly need the tools.  I'm using the VM simply as a Linux development environment.

In the meantime, if I *do* find a solution to my problem, I'll share it with others.

Thanks,
--naijireja

---

### Post by naijireja on 2007-07-15
Hi TheExplorer,

I took your advice and installed VirtualBox on my Windows host, and installed Ubuntu as the guest OS.  The Ubuntu virtual machine seems far more speedy and responsive than it did when it was running VMWare.  I think I'll use this hypervisor from now on when I want to set up development virtual machines.

Thanks,
--naijireja

---

