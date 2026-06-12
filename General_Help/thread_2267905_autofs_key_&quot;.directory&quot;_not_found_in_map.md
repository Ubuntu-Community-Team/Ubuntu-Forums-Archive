---
title: "autofs: key &quot;.directory&quot; not found in map source(s)."
date: 2015-03-04
forum: General Help
---

### Post by Kenneth_Harder_Ras on 2015-03-04
Hello,

Can somebody explain to me what the following error messages means? I have tried google, but with no luck.

attempting to mount entry /home/htpc/nfs/.directory
lookup_mount: lookup(file): looking up .directory
key ".directory" not found in map source(s).
dev_ioctl_send_fail: token = 13
failed to mount /home/htpc/nfs/.directory
st_expire: state 1 path /home/htpc/nfs/
expire_proc: exp_proc = 139703772772096 path /home/htpc/nfs/
expire_cleanup: got thid 139703772772096 path /home/htpc/nfs/ stat 0
expire_cleanup: sigchld: exp 139703772772096 finished, switching from 2 to 1
st_ready: st_ready(): state = 2 path /home/htpc/nfs/

I get the same error on both a clean ubuntu minimal 14.04 and the latest kodibuntu.

I had autofs working on my previous install, but had to reinstall because of a failed attempt to optimize my htpc.

If mounted with mount ...., the mounts work perfectly.

---

### Post by bapoumba on 2015-03-05
*Thread moved to **General Help**.*

---

