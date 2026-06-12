---
title: "setting up local network"
date: 2005-04-16
forum: General Help
---

### Post by alainhenry on 2005-04-16
I now have 2 PC's at home, and a small DSL router (D-link DSL 504).  I would like to set-up a small LAN, to have these two PC's communicate to each other and to the Internet.  I assume Samba would do the job, but if I keep to Linux-only, I guess other, simpler, software would be enough.  Could someone point me some how-to or software?  This is a new area for me, so I don't know where to start.  

I notice samba-common is in Hoary's default install.  Would that be enough ?

Thanks

Alain

---

### Post by joshmachine on 2005-04-16
[QUOTE=alainhenry]I now have 2 PC's at home, and a small DSL router (D-link DSL 504). I would like to set-up a small LAN, to have these two PC's communicate to each other and to the Internet. I assume Samba would do the job, but if I keep to Linux-only, I guess other, simpler, software would be enough. Could someone point me some how-to or software? This is a new area for me, so I don't know where to start. 

I notice samba-common is in Hoary's default install.  Would that be enough ?

Thanks

Alain[/QUOTE]

It depends on what you want to do with the PCs.  Samba is a simple solution if want to share files.  The router should take care of the internet access.

If you want to share files, each machine that you want to have shares on will have to have the "samba" package installed.  If there is a machine that you want only to browse shares, you don't need this.

Cheers

---

