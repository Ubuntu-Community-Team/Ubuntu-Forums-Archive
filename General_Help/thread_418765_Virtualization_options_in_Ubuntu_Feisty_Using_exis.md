---
title: "Virtualization options in Ubuntu Feisty: Using existing XP installation"
date: 2007-04-22
forum: General Help
---

### Post by sshetye on 2007-04-22
Hi folks,

I'm running Feisty (7.04) and had a few questions.

1) I currently dual boot XP and Ubuntu. I want to boot into the 'real' XP installation from inside Ubuntu via a virtual machine. VMware currently support it (it uses the real partition as a data source instead of a virtual disk). Question is does KVM or VirtualBox support something like this too?

2) Is there a performance comparison between KVM, VMware and Virtualbox? What about including 3d acceleration? (VMware support 3d I think ... need to edit the config. file by hand though).

3) Is there a good GUI front end for KVM? Also, is KVM the same as Qemu/Kqemu ??

Thanks guys !!

FYI, I need to boot into XP for office usage and re-installing XP into a virtual partition isn't an option since the IT dept. has it's own custom XP image which they cannot distribute.

---

### Post by the8thstar on 2007-04-22
> 1) I currently dual boot XP and Ubuntu. I want to boot into the 'real' XP installation from inside Ubuntu via a virtual machine. **VMware currently support it (it uses the real partition as a data source instead of a virtual disk)**. Question is does KVM or VirtualBox support something like this too?

Wow, how did you do this?

---

### Post by MRiGnS on 2007-04-22
[http://virtualbox.org/wiki/Migrate_Windows](http://virtualbox.org/wiki/Migrate_Windows)

---

### Post by sshetye on 2007-04-22
> **the8thstar said:**
> Wow, how did you do this?

Open an existing virtual machine -> add hard disk -> use physical disk -> pick you physical partitions -> boot OS on real partition inside VM :)

The caveat is that to "pick physical partition" you need admin privileges ... running "sudo vmware" kills a lot of permissions so that VM can't be accessed by a usual user - which is a bummer. 

I need to access that VM always as root which I'm trying to move away from ... until I figure out a way of not fubar'ing the file permissions.

---

### Post by Ziggy72 on 2007-04-22
I used to dual boot Windows XP and Ubuntu but I abandoned that eventually because it was really inconvenient to have to reboot every time I needed to change operating systems. I now use Ubuntu Feisty running as a VMWare Desktop guest on Windows XP Professional and that is much more convenient because both operating systems and their programs are immediately available by pressing a hot key combination.

There are a number of posts about the use of virtual systems on this forum. Have a look at [post]395130[/post] for some comments about VMWare and VirtualBox and you'll find some links there. I have no experience of KVM. VMWare Desktop which I use is very powerful - the only downside is it's price. If that's too expensive you should try VirtualBox. I used VirtualBox a while ago and at that time it was still in active development and still had a few issues that weren't very satisfactory but was still usable - worth your while giving it a try and if you don't like it, it's easy to uninstall.

---

### Post by sshetye on 2007-04-23
> **sshetye said:**
> The caveat is that to "pick physical partition" you need admin privileges ... running "sudo vmware" kills a lot of permissions so that VM can't be accessed by a usual user - which is a bummer. 

I need to access that VM always as root which I'm trying to move away from ... until I figure out a way of not fubar'ing the file permissions.

Ok, figured out a way to use the virtual machine as a regular user (instead of always running it as root). 

```
sudo adduser <your_normal_user_name> disk
```

This way vmware running with your 'normal' user privileges can access the physical partitions to boot into. I heard a tip about making a separate h/w profile to avoid M$'s WPA to kick in forcing another activation on the same install. What pain this WPA is ... after paying M$ a ton of money for all the licenses ... sigh.

Anyone out there figured out how to run VirtualBox or KVM to use the physical partition? MRiGnS, the link you mentioned indicated the likely problems, but doesn't really explain how to configure VirtualBox for it. That implies that it's at least possible ...

Ziggy72, thank ! That's pretty similar to what I've managed to setup now. I'm wondering if KVM is worth a shot since everyone is raving about Feisty+KVM. If the performance differences are marginal then I'd prefer the simple setup of VMWare ... lets see !

Ubuntu rocks ...

---

### Post by Bluecube on 2007-05-19
sshetye - I was very interested to read that you managed to boot a virtual machine using a currently installed Windows partition. I'm trying to do that myself (albeit with Vista) and the VM is crashing on startup. I presume that this is because the VM machine is different from the initial hardware that Windows was installed on. Did you have to do anything to fudge a boot or did it work straight off?

TIA

---

