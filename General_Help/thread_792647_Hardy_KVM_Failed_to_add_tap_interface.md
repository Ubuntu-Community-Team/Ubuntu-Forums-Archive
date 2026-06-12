---
title: "Hardy KVM Failed to add tap interface"
date: 2008-05-13
forum: General Help
---

### Post by srodden on 2008-05-13
(Was posted to Virtualisation section a week ago but no replies yet. Trying here!)

Hi folks,

I have a pretty vanilla Hardy install and I started playing around with KVM/QEMU tonight. I've set up XP and Vista VMs and they work a treat. While sorting out networking, I've run into a problem. Following the instructions on the 'official' page allows me to set up a bridged interface br0 which virt-manager recognises (the details on the VM show br0 as the interface) however when I start the VM I get an error as pasted below. My user account is a member of the kvm and libvirtd groups.

This looks like the CAP_NET_ADMIN issue from kernel 2.6.18+ as documented on this link: [http://calamari.reverse-dns.net:980/...4f83c281117a86](http://calamari.reverse-dns.net:980/...4f83c281117a86)

I figure this would've been addressed for the Hardy release so I'm guessing I've missed or messed something. Any advice, please? I do not wish to have to run the VMs with root privs.

Thanks,
Sean

Error starting domain: virDomainCreate() failed Failed to add tap interface 'vnet%d' to bridge 'br0' : Permission denied

Traceback (most recent call last):
File "/usr/share/virt-manager/virtManager/engine.py", line 480, in run_domain
vm.startup()
File "/usr/share/virt-manager/virtManager/domain.py", line 379, in startup
self.vm.create()
File "/usr/lib/python2.5/site-packages/libvirt.py", line 240, in create
if ret == -1: raise libvirtError ('virDomainCreate() failed', dom=self)
libvirtError: virDomainCreate() failed Failed to add tap interface 'vnet%d' to bridge 'br0' : Permission denied

---

### Post by cfmunster on 2008-06-24
This is indeed the bug in 2.6.18 +  kernels:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=412941](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=412941)

There have been a few other threads about the issue, no success on a solution yet. The Debian.org bug report has some good details if you read through the email chain.

---

### Post by srodden on 2008-06-25
Thanks for the post. It seems strange to me that this has passed several kernel patches (x.x.18-24) being Canonical's chosen virtualizer and yet there isn't a workaround. Also seems strange that there aren't more people posting on the forums here about it. Does no one else use KVM? Certainly there seem to be many more threads about VirtualBox and VMWare.

---

