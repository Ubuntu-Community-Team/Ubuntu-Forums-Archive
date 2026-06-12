---
title: "Setting up a VM on headless server (Xen)"
date: 2015-12-01
forum: General Help
---

### Post by Ackis on 2015-12-01
Having never played with a VM before I've been looking at suggestions for a vm.  It looks like Xen may be the easiest for a beginner based on the wiki ([https://help.ubuntu.com/community/VirtualMachines](https://help.ubuntu.com/community/VirtualMachines)) - I'm just wondering what are the risks doing this remotely?

One of the first steps for Xen is to reboot and have grub load it up - wouldn't that mean I lose access to the machine for SSH sessions?

---

### Post by TheFu on 2015-12-04
Xen runs a modified kernel (at least it used to).  I've had Xen refuse to boot after a kernel update and had to drop back to an older kernel for a few weeks. Stopped using Xen around 2011-ish after running it for 3 yrs. Don't regret that at all.

KVM is easier, IMHO, for server-on-server VMs. KVM is part of the Linux kernel and tested in the same way. I've **NEVER** had issues in 5+ yrs of KVM use that prevented a system to boot.  

With KVM, load libvirt and run virt-manager on a workstation from anywhere in the world to manage VMs over ssh. In theory, this should work for Xen VMs too.

The only "pro tip" I have is that you should manually create the bridge(s) you want, never use the built-in bridges from any KVM/Xen/libvirt config. I don't know why, but their bridges seem to hiccup from time to time, but the manually created bridges do not - ever.

On a headless server, something like proxmox might be easier. It is a full OS load and has a web-management setup for those that prefer point-in-click. Of course, you'll need to physically install proxmox on the server while being in the same room.

Hopefully, others who are pro-Xen will reply so you get 2-sides of the Xen story.

---

