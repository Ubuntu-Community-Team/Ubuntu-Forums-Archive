---
title: "Nautilus behavior in Hardy changes over NFS mount"
date: 2008-04-30
forum: General Help
---

### Post by TallMatthew on 2008-04-30
This behavior has changed since Gutsy.

A nautilus window on a NFS share will not update file attributes if they are being changed on the NFS server.  Too, if a file is added or removed, again on the file server, this will not update until the window is reloaded.

However, if you add or remove a file from the NFS client (the workstation where the window is open), this change will be reflected in the open window immediately.  

For example

/nfsmount is mounted on nfsclient from nfsserver

Open /nfsmount in a nautilus window.

Logon to nfsserver.  Touch /nfsmount/x.  x will not appear in the open window.

On nfsclient, touch /nfsmount/y.  y will appear immediately in the open window.  x still does not appear.

Anybody know whether this is a feature, a bug, or just weirdness?

---

