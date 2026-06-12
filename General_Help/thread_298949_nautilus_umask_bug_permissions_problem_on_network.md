---
title: "nautilus umask bug permissions problem on network"
date: 2006-11-13
forum: General Help
---

### Post by sitedesign on 2006-11-13
I have our office set-up with Ubuntu workstations now connecting to an Ubuntu  file server. Very nice network.

I have used sshfs for sharing files on the server.

One problem I have now is that there is a bug in nautilus that creates new folders and files with default permissions even though I have the umask set to 007. If I create the folders and files using openoffice or another file manager it works fine.
But if I use nautilus the folders get created with limited permissions.

Does anyone know when this is likely to get fixed and arrive in Unbuntu updates?

link to bug:
[http://bugzilla.gnome.org/show_bug.cgi?id=327249](http://bugzilla.gnome.org/show_bug.cgi?id=327249)

---

