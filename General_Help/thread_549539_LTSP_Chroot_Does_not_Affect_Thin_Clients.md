---
title: "LTSP Chroot Does not Affect Thin Clients"
date: 2007-09-12
forum: General Help
---

### Post by gam3r4eva on 2007-09-12
A few of us at our school have a set up a Linux lab.  Our server runs Edubuntu 7.04 (x86_64) and uses about 15 pentium 2's for the thin clients.

We have been able to get all of the thin clients to find the server at boot, and correctly boot into Edubuntu.

The only problem we have is that any changes made in the chroot (/opt/ltsp/i386) do not seem to affect the thin clients at all.

I can run commands inside the chroot, such apt-get install "X," but after successfully running this command and booting the thin clients, the thin clients do not have the "X" installed on them.

However, any changes made on our server *do* affect the thin clients.  If I apt-get install "Y" on the server, after booting the thin clients, they "Y" installed on the as well.

Does anyone know why this is, or has anyone experienced this before?  Any and all help would be appreciated.  If any more information is needed I will gladly supply it.

Thanks

---

