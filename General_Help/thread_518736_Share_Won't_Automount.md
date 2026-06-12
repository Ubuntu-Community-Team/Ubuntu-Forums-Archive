---
title: "Share Won't Automount"
date: 2007-08-06
forum: General Help
---

### Post by Ingla on 2007-08-06
Hello.

I 've set up NFS file sharing between two machines; One is running Ubuntu Feisty and the other Ubuntu Dapper. Each machine is both a server and a client for the other.

Everything works fine.

Just one minor thing: The Dapper box won't automount the shared folder. The line in fstab is:

10.0.0.139:/home/aba /media/shared nfs rsize=8192,wsize=8192,timeo=14,intr auto

This sort of setup works in Feisty and the share is mounted there on boot. On Dapper it needs to be mounted manually (which works with no problem).

Thanks.

---

