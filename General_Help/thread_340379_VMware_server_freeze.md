---
title: "VMware server freeze"
date: 2007-01-17
forum: General Help
---

### Post by mygravity on 2007-01-17
Hi.

Have VMware server 1.01 running with a Windows XP installation. 

Using VMware server I am able to run Internet Explorer and view websites running from my local machine. Everything works fine for about 5 minutes then the whole computer will freeze:
 - Gnome system monitor shows no processor activity
 - Gnome clock works as normal (minutes keep ticking over)
 - mouse cursor can still move, but not select anything
 - can't change between workspaces
 - can't switch to a terminal using Ctrl-Alt-F1-5
 - can't logout using Ctrl-Alt-Backspace

The system will [COLOR="Blue"]unfreeze about 5 minutes later[/COLOR]. Anyone having similar experience or know how to fix this?

SYSTEM DETAILS:
DELL Precision 390
Am using Ubuntu Edgy Eft with all updates installed.

Many thanks

Andrew

---

### Post by Canis familiaris on 2007-01-17
I am not sure, but probably thus happens due to the fact that your VM is maybe using the Host OS entire memory. Try reducing the Guest OS RAM.
If this does not work, try to reinstall VMWare.

---

### Post by gammal on 2007-01-24
It hardly has anything to do with memory. I'm experiencing the same problem, and the only clue I have is messages like this one being printed on the console:
```
[xxxxxxxx.xxxxxx] unregister_netdevice: waiting for vmnetX to become free Usage count: 1
```
I found many other people complaining from the same problem, with no working solution so far.

---

### Post by anders on 2007-03-06
You can add me to this list. I'm using Edgy Eft on a Dell Latitude D620, Dual Core, Nvidia graphics. I'm running Win XP as a guest OS inside VMWare Server 1.02 (upgrading from 1.01 to 1.02 didn't seem to make a difference)

---

### Post by bOUNCeErR on 2007-03-13
This seems to be a kernel issue. I have just manually compiled 2.6.18.8 kernel (please see [[COLOR="Red"]this link[/COLOR]]("http://www.howtoforge.com/kernel_compilation_ubuntu")) if You don't know how). After that my VMware is running for 1 hour without any problems. Previously it hung after max. 3 minutes.

Regards,
bOUNCeErR

---

### Post by veloce on 2007-03-13
> **gammal said:**
> It hardly has anything to do with memory. I'm experiencing the same problem, and the only clue I have is messages like this one being printed on the console:
```
[xxxxxxxx.xxxxxx] unregister_netdevice: waiting for vmnetX to become free Usage count: 1
```
I found many other people complaining from the same problem, with no working solution so far.

I'm using vmware server 1.01 with no such problems.  However, I have customised the virtual network settings.  Based on the error message reported, I would try eliminating all the virtual networks that you are not using.  See if that improves things.

---

### Post by ntt on 2007-03-15
Hi all,

same problem here.

I'm using Kubuntu 6.10, VMware server 1.0.2 on a Dell D620 (Intel graphics).

The bottom line for me is that the whole X environment freezes under network I/O of the guest OS.

In my case the problem is usually triggered by DB queries, but I've found that any kind of network I/O burst of the guest OS will soon or later freeze the PC.

BTW, "freeze" is not the proper term here... when my X interface locks up, I'm still able to log in via SSH and to operate the PC as normal. CPU usage under this conditions is always very low (almost zero, in fact) and I can't find an exact cause for the problem.

Sometimes you can even access the console locally, but most of the times you can't (input frozen, except - from time to time -  the mouse pointer).

What makes me mad is that a colleague of mine with the very same PC model but using Debian Etch (kernel 2.6.18) doesn't have any problems at all.

In the recent past I've had the same problem with an ACER Intel dual-core and VMware server 1.0.1, so it's not related specifically to my current HW.

The only workaround I've found so far is to disable ACPI in the kernel boot parameters; doing so will bring up only 1 cpu, and the sysytem will be absolutely stable.

Tried also to disable 1 core in the BIOS of the PC, but 1 core with ACPI enabled still hangs under the a.m. circumstances.

I believe this to be a kernel problem; is there a way to install an Ubuntu kernel 2.6.18? I can't find any in the standard repositories (not even multiverse).

Thanks in advance for any hints, and sorry about the lengthy post.

---

### Post by anders on 2007-03-15
There are many threads on this issue in the vmware support forums:

[http://www.vmware.com/community/](http://www.vmware.com/community/)

A few have reported success when disabling som acpi or dual core features but there doesn't seem to be anything conclusive. It seems to be related to Intel Core Duo and curiously enough many seem to be using Dell laptops, dont know if it's a coincidence. 

Let's just hope there will be a real solution to this problem some time soon.

---

### Post by ntt on 2007-03-15
Yes, saw that thread in the VMware forums, but as you say it's not conclusive at all.

All I know is that this problem affects a number of distributions (especially SuSE and Ubuntu), with kernels ranging from 2.6.17 all the way to 2.6.19, but always on dual-core processors.

Heck, my colleague - sitting next to me with the very same PC model and VMware setup - is NOT affected. He's using Debian, though, and not Ubuntu. And he's laughing at me...

Furthermore, whenever using the very same virtual machine(s) on single-processor laptops nothing bad happens! I have two other notebooks running Kubuntu 6.10 and VMware server 1.0.2 (an Athlon64 and a Pentium Mobile something), and they're NOT affected by the problem at all.

Don't know what to say... my last hope is to compile a custom kernel, stripping away all of the unnecessary frills, and see whether this helps. But I want to try with a 2.6.18, at least.

Ah, one last bit: I was investigating what the difference is between a stock Linux kernel and its Ubuntu counterpart; in the Ubuntu kernel section someone recompiled a kernel in order to fix problems with dual-core processors. He/she (?) says that a certain set of standard Ubuntu patches ("ck", if I remember correctly) was causing problems due to aggressive optimizations.

Don't know if that is A) true and B) possibly helpful for us VMware users, but I'd like to give the suggestion a try, and see what happens.

Thanks.

---

### Post by anders on 2007-03-15
Yes, compiling a kernel from the vanilla sources would be first on my list of things to try. It seemed to have solved it for bOUNCeErR in this thread. The freeze occurs seldom enough for me and I don't use vmware that much so I haven't bothered trying that. If you do go that path I would love to hear if it was a success though.

---

