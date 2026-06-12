---
title: "shared folder unable to be mounted"
date: 2008-05-02
forum: General Help
---

### Post by fycloops on 2008-05-02
I am trying to share folder between two pcs on my lan.

Hardy 32 and Hardy 64.

I have two HDDs and I am trying to share two folders on the second HDD fs=fat32.

The other pc (the Hardy 32) can see the folders in places/network but says "unable to mount".

Have samba installed.

Any ideas?

---

### Post by fycloops on 2008-05-04
I found that I could share them after I mounted them with fstab and then edited smb.conf to allow non-owners to share files.

---

