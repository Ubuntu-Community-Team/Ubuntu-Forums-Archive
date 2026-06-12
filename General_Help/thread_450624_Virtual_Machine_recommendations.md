---
title: "Virtual Machine recommendations"
date: 2007-05-21
forum: General Help
---

### Post by ezrollers on 2007-05-21
Hello,

I've got quite a few problems running ubuntu, so I've decided to run a XP on a virtual machine.

Any suggestions?

I know about VMware.

I also know about Xen, but I have struggled to find a decent howto for 7.04

TIA

---

### Post by tgm4883 on 2007-05-21
vmware or virtualbox.  Depends on it your running 64 bit or 32 bit as 64 bit is easier to run vmware.  vmplayer needs a prebuilt virtualmachine which can be done for free at easyvmx.com  otherwise you will need vmworkstation

---

### Post by nimrod_abing on 2007-05-23
Hello,

I just want to bring into attention that VMWare Server is also available from Applications/Add Remove menu item on Feisty provided you have an up-to-date system. 

VMWare Player requires a pre-built/pre-configured VMX image whereas VMWare Server allows you to create VMX images from scratch. If you do not need to use snapshots tree or VMWare Teams but you need to be able to create VMX images, then VMWare Server should suffice.

I have been itching to try Xen virtualization but it's not as straightforward as inserting a CD, booting up the VM and installing the guest OS on VMWare.

Links:

dom0 - Ubuntu Feisty Fawn, domU - Ubuntu Edgy Eft:
[https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuFeisty](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuFeisty)

dom0 - Ubuntu Dapper Drake (should also work with Feisty as dom0), domU  - Windows XP:
[http://www.planetjoel.com/viewarticle/568/HOWTO%3A+Windows+XP+running+under+Xen+3.0+on+Ubuntu+Dapper+Drake](http://www.planetjoel.com/viewarticle/568/HOWTO%3A+Windows+XP+running+under+Xen+3.0+on+Ubuntu+Dapper+Drake)

So far I have been happy with VMWare server, but I really miss the snapshot tree feature that comes with VMWare Workstation.

---

