---
title: "VMware Server never stops asking to be upgraded"
date: 2007-12-04
forum: General Help
---

### Post by altonbr on 2007-12-04
I have a fresh install of Gutsy with Canonical's partner repository enabled.

Instead of compiling VMware server from scratch like I always do, I installed it from the repositories.

It installs *and* works, but Synaptic always has that orange icon in the top-right corner asking for VMware Server to be upgrade.

No matter how many times I read or accept the VMware license, it always comes back.

Update Manager says: "From version 1.0.4-1gutsy1 to 1.0.4-1gutsy1 (Size: 75.0 MB)"

I've also 'purged' the install and re-installed, but to no avail.

Any advice or is this a known bug?

---

### Post by digitalbenji on 2007-12-04
I've got the same problem on Feisty.  I've started ignoring it, but it would be nice to resolve.  Next time I'll probably install vmware manually.

---

### Post by altonbr on 2007-12-04
> **digitalbenji said:**
> I've got the same problem on Feisty.  I've started ignoring it, but it would be nice to resolve.  Next time I'll probably install vmware manually.

If you do, make sure to follow this guide: [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server). There's an ugly hack for Gutsy because VMware Server 1.0.x doesn't support the brand new 2.6.22 kernel yet.

---

### Post by toobuntu on 2007-12-06
I filed a bug report filed on Launchpad about this issue, among others.

[HTML]https://bugs.launchpad.net/ubuntu/+source/vmware-server/+bug/173261[/HTML]

---

