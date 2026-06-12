---
title: "Chroot or virtualization?"
date: 2007-02-13
forum: General Help
---

### Post by StarsAndBars14 on 2007-02-13
I have things that I need to work with in a secured environment.

In this event, would it be better to chroot a second operating system, accessible from my home directory, or use something like VMWare Server to run the system?

Someone please explain to me the differences between the two (if any exist.)

Thanks.

(PS:  I've just come across this:  
[http://linux-vserver.org/Welcome_to_Linux-VServer.org](http://linux-vserver.org/Welcome_to_Linux-VServer.org)

Does anyone here have experience with this patch?  Does it work well or not?)

---

### Post by nereid on 2007-02-13
I would think that a virtualized environment is better than a chrooted one. The chrooted environment allows, if cracked, access to the server. In a virtualized environment you can only change the virtual server, which can be easily rebooted.

---

### Post by StarsAndBars14 on 2007-02-14
Thank you, I think I've made my decision.  

I'll use the latest stable linux-vserver patch with Grsecurity enabled.
I think it'll work instead of either AppArmor or SELinux anyways (in the case of the latter, not work better -- but be updated more frequently for Ubuntu and just might have a chance of working without me wanting to pull my hair out.)

---

### Post by lamego on 2007-02-14
> The chrooted environment allows, if cracked, access to the server.
The chroot is enforced at the kernel level, it can't be cracked that's why its commonly used  as a security option for a lot of services
The major gain of using VM versus chroot is that  you can easly save/load system snapshots (VM images).
The major loss is that a VM will use much more system resources to run the virtual system.

The best option depends a lot on what you plan to do on that "secured" sytem.

---

