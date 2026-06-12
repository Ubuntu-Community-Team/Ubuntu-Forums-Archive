---
title: "VMI-supported in Desktop version?"
date: 2007-04-21
forum: General Help
---

### Post by tom.chau on 2007-04-21
Hi,

I would like to ask if the VMI-support (VMWare) is also in Desktop edition?
It is explicitly described for Server edition but not in Desktop edition....

Do i need something to do for it works in Desktop edition (e.g., install edition package, select VMI-kernel in boot menu, etc.)?

Thanks in advance.

Tom

---

### Post by sewmyheadon on 2007-04-21
Tom,

I'm wondering the same thing and searched around the forums earlier, but didn't find a straight answer to the question yet.  So Google turned up this:

[http://onlyubuntu.blogspot.com/search/label/upgrade%20ubuntu%20egy%20to%20feisty](http://onlyubuntu.blogspot.com/search/label/upgrade%20ubuntu%20egy%20to%20feisty)

> "Kernel Virtual Machine: On x86 systems with the Intel VT or AMD-V extensions, Kernel-based Virtual Machine support (KVM) allows users to run multiple virtual machines running unmodified Linux. Each virtual machine has private virtualised hardware: a network card, disk, graphics adapter, and so on. We have also added VMI support, which provides optimised performance under VMWare."

---

### Post by tom.chau on 2007-04-21
Hi Eric,

Thanks for your information. However, I am confused by the ubuntu overview whether the VMI is only supported in Server edition or available in both version.

I search the forums as well. There is a post saying that the KVM is available in both version but I am not sure about VMI. I am new to virtualization but I think KVM and VMI are different...

Tom

---

### Post by kimus on 2007-04-21
I can't enable paravirtual kernel support on a VMWare 6.0 guest. The VMI support in the kernel must be supported.

I'm using ubuntu 7.04 so this should be enabled. How can I check if VMI is enabled?

---

### Post by sewmyheadon on 2007-04-21
> **tom.chau said:**
> Hi Eric,

Thanks for your information. However, I am confused by the ubuntu overview whether the VMI is only supported in Server edition or available in both version.

I search the forums as well. There is a post saying that the KVM is available in both version but I am not sure about VMI. I am new to virtualization but I think KVM and VMI are different...

Tom

KVM and VMI are different, but from what I can tell KVM can be added and VMI is a kernel-level thing that is resident in all distributions of Feisty.

**Got the following quote from here:**
[http://searchenterpriselinux.techtarget.com/originalContent/0,289142,sid39_gci1251013,00.html](http://searchenterpriselinux.techtarget.com/originalContent/0,289142,sid39_gci1251013,00.html)

> VMI support, which currently provides optimized performance for paravirtualized Linux OSes under VMware, has also been added the Linux mainline kernel and will be included in Ubuntu.

---

### Post by pooslinger on 2007-04-26
2.6.20 KVM (_buntu 7.04 release)

2.6.20 VMI VMWare workstation 6 needed

Edit: I stand corrected.  VMI is compiled into 7.04 and works very well.

---

### Post by darwin_te on 2007-06-27
The paravirtual kernel support is available only when running Linux guest.  If you're running Windows guest, it is disabled.  Also your Linux guest kernel should have support for VMI.

---

### Post by adarshj on 2008-03-12
> **kimus said:**
> I'm using ubuntu 7.04 so this should be enabled. How can I check if VMI is enabled?

You can check that using dmesg. Check out this Knowledge Base article from VMware for more details: [http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003644](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003644)

---

