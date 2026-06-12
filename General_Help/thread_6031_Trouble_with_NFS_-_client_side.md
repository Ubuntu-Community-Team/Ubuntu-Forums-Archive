---
title: "Trouble with NFS - client side"
date: 2004-11-24
forum: General Help
---

### Post by TimL on 2004-11-24
Does anyone have any experience with mounting an NFS export from another machine?

I've been trying to do this for the last couple of days, but whenever I try to mount the share, I receive this error message:

mount: RPC: Program not registered

I've tried installing the nfs-common package, but I still can't get this to work.

I know the NFS server is working ok, as I used to be able to connect from a Fedora machine to this share.

---

### Post by TimL on 2004-11-24
I managed to fix this - it wasn't set up properly on the server-side.  :oops:

---

