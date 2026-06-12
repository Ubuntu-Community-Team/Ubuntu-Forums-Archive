---
title: "Clock in a Linux Guest Runs More Slowly Than Real Time"
date: 2007-04-21
forum: General Help
---

### Post by bbalazs on 2007-04-21
Hi Everybody!

I've encountered a very exciting issue. For testing purposes I use VMware Server from XP, and install Ubuntu under that. The guest linux (ubuntu, mandriva also) is very slow.
I've found an article about this issue at VMware, and they advice to use some options in grub at kernel to disable apic and smp (noapic and nosmp), but it doesn't help.

[http://kb.vmware.com/selfservice/dynamickc.do?externalId=1420&sliceId=2&command=show&forward=nonthreadedKC&kcId=1420](http://kb.vmware.com/selfservice/dynamickc.do?externalId=1420&sliceId=2&command=show&forward=nonthreadedKC&kcId=1420)
[]("http://kb.vmware.com/selfservice/dynamickc.do?externalId=1420&sliceId=2&command=show&forward=nonthreadedKC&kcId=1420")

It'S also said that I have to compile the kernel with changing a special value in a source file, but the value is OK. (I have to replace it  1000 -> 100)

Does anyone have any suggestion? It's an absolutely faulire.

Did anyone experince with this?

Thank you guys

---

### Post by sonofusion82 on 2007-04-21
yes, as explained in the article, virtual machine's emulated hardware clocks and interupts is less predictable than real hardware clock due to host OS scheduling. it happens to both VMWare and also Virtual and also to any guest OS including windows.one solution is to install the virtual machine add-ons and drivers in the guest OS. but when the add-on are not available for the guest OS, u can probably install NTP server on host machine and the NTP client in the guest OS to sync with clocks. :)

---

