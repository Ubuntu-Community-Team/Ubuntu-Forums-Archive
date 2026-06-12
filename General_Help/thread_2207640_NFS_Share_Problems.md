---
title: "NFS Share Problems"
date: 2014-02-24
forum: General Help
---

### Post by kevinkelly5557-b on 2014-02-24
Hi there,

I'm doing something silly and have gotten myself into a muddle with my NFS shares, I had these working before 

SERVER 

/etc/exports
/media/TB2B/TB2B            192.168.0/24(rw,no_root_squash,sync,no_subtree_check)

Folder 

/media/TB2B/TB2B drwxr-xr-x 7 kevin kevin 4096 Feb 21 17:27 TB2B

CLIENT

/etc/fstab
192.168.X.X:/media/TB2B/TB2B      /media/TB2B/TB2B nfs4 rsize=8192,wsize=8192,timeo=14,intr

Folder

/media/TB2B/TB2B drwxr-xr-x 3 kevin kevin 4096 Feb 21 17:32 TB2B

sudo mount -a

mount.nfs4: access denied by server while mounting 192.168.X.X:/media/TB2B/TB2B


Thanks! :)

---

### Post by kevinkelly5557-b on 2014-02-24
Rebooted client and it worked >_<

Thanks for having a look if anyone did :)

---

