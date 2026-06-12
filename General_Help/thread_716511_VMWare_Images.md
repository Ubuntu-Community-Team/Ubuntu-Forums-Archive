---
title: "VMWare Images"
date: 2008-03-06
forum: General Help
---

### Post by TigerWolf on 2008-03-06
Is it possible to get a VMWare image of ubuntu and somehow copy it onto a partition so that it runs on its own outside of VMWare?

---

### Post by DavidTangye on 2008-03-06
I am not sure that it would be worth the trouble, as the ubuntu system in a vmware vm will be as installed for the vmware (virtual) machine, ie the graphics, and network card etc drivers will not be correct for your real machine.

---

### Post by TigerWolf on 2008-03-06
Its always possible to configure them to match the new system. I want to know if it can be done.

---

### Post by DavidTangye on 2008-03-06
> **TigerWolf said:**
> Its always possible to configure them to match the new system. I want to know if it can be done.My guess is yes:
[LIST=1]
[*]Copy the entire VM filesystem into a real partition via a VM network link.
[*]Add an entry in the real /boot/grub/menu.lst to boot it (especially in single user mode)
[*]Boot it in single user mode, and run dpkg-reconfigure on a few packages including the network adapter and graphics stuff etc. Essentially you need to do **everything** that the installation scripts do, and I see this as a bad way to go. It seems to me to be more common sense to install using the installers scripts, ie do a standard install. Why would you not want to just use the standard installer?[/LIST]

---

