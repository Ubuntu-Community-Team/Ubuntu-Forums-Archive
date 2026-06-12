---
title: "will running ubuntu through windows host with virtualbox resolve linux driver issues"
date: 2013-07-09
forum: General Help
---

### Post by ivanzypher on 2013-07-09
Hi
Does hardware run through drivers on host or guest os?
i am having power and cpu and fan issues with linux and wondering whether im best running through windows host
thanks

---

### Post by Old_Grey_Wolf on 2013-07-09
Virtualbox uses the host OS drivers.

---

### Post by dannyboy79 on 2013-07-09
NO, whether you run Ubuntu straight on the hardware OR through a VM, if you're having issues with driver support, cpu throttling and or power usage than it boils down to the linux kernel or the linux drivers for that specific hardware.

Old_Grey_Wolf- so you're saying that if i boot ubuntu up in a VM which is on a Windows Host, that the windows drivers somehow know how to communicate and work with linux?

---

### Post by The Cog on 2013-07-09
No, it's the other way round. If you use Linux in a VM on Windows, the VM is just a Windows application and uses the Windows operating system with its drivers to talk to the hardware. 

The Linux guest only sees hardware that the VM pretends is there which is probably nothing like the actual real hardware. For example, as I remember, VirtualBox allows you to configure up to 4 network cards, each being one of about six different types.

---

### Post by Old_Grey_Wolf on 2013-07-09
Virtualbox is a Type 2 Hypervisor that creates virtual machine environments and coordinates calls for CPU, memory, disk, network, and other resources **through** the host OS. What the VM thinks is hardware is actually a set of standard Virtualbox divers that interface with the actual host OS.

PS: That is why the are different versions of Virtualbox for Windows and Linux hosts. Virtualbox must be able to work with the host OS.

---

### Post by ivanzypher on 2013-07-09
I can confirm success with virtualbox. It seems to be utilising the underlying o.s drivers. My fans and idle cpu/gpu temps aren't going crazy and I'm happy for that!

---

### Post by Old_Grey_Wolf on 2013-07-09
> **ivanzypher said:**
> I can confirm success with virtualbox. It seems to be utilising the underlying o.s drivers. My fans and idle cpu/gpu temps aren't going crazy and I'm happy for that!

I hope you will be able to run Ubuntu without using a VM on whatever hardware you have sometime in the future. In the meantime, enjoy using what works.

---

