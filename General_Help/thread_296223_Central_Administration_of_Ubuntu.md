---
title: "Central Administration of Ubuntu"
date: 2006-11-09
forum: General Help
---

### Post by thembimoyo on 2006-11-09
Hi,

I am an ICT Manager for an Academic Institution. I LOVE Ubuntu and want to centraly depoly, and Manage it on 450 Machines of diffrenet specifications. I also want administor user names and passwords using LDAP Please advise me on the best way forward.

---

### Post by kidders on 2006-11-09
Hi there,

Afaik, Ubuntu doesn't provide any "special" way of centrally administering a large network, so you would do it in essentially the same way any other Linux distribution does. There are rather a lot of useful HOWTOs around for various distros, that will help you identify good software choices, as well as any potential traps. As you may know, documentation for Debian-like systems is perhaps most useful for Ubuntu users.

I suppose the three most important things to have in place for Linux networks with large user bases are...

[LIST]
[*]Shared user storage (perhaps with an NFS share mounted at /home)
[*]A local package repository (so you don't have to keep re-downloading the same stuff over and over)
[*]Centralised account management (Imo, LDAP is the best choice, as you seem to have identified already)
[/LIST]

You might also like to consider making some slight modifications to the way Ubuntu handles things like application settings. You could, for instance, centralise files like /etc/fstab and so on, to make system tweaks easier to propagate in the future. In my experience, things like udev, pmount, and related bits & pieces very often need post-deployment tweaking.

**Edit:** If I were you, I would also spend some time thinking about how decisions you make will affect your ability to try other Linuxes out on the network in the future. There are some irritating little things that can crop up from time to time, that can make doing this difficult. Mandriva, for example, is (in Ireland at least) a pretty common choice for academic institutions. It would be ideal if you could leave the door open to experiments like that in the future :-)

---

