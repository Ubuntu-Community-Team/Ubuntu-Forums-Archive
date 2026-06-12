---
title: "nfs shares in /etc/fstab not mounted at boot"
date: 2015-02-24
forum: General Help
---

### Post by robert-nurnberg on 2015-02-24
The following bug appeared on my ubuntu 14.04 machine (regularly updated) in the last month or so.

nfs shares listed in /etc/fstab are not mounted during the boot process, but can be mounted manually after booting.

The problem appears to be that the client wants to use NFS4, which the server does not provide. I have found the following work-around:

In /etc/stab explicitly list the nfs-version to use. E.g.

```
server:/foo    /bar      nfs nfsvers=3,rw,bg,nosuid,soft 0 0
```

Note that replacing  nfsvers=3 with nfsvers=4 will give the buggy behaviour described above.

I post this here so that other people with the same problem can find the work-around.

I guess I should report this as a bug on launchpad, but I am not sure how to do that.

---

### Post by slickymaster on 2015-02-24
Did you already saw this bug report: [NFS shares in FSTAB no longer mount at boot]("https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1385846")?

---

