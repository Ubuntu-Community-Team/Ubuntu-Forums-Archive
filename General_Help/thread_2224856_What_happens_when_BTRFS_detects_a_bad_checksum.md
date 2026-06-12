---
title: "What happens when BTRFS detects a bad checksum?"
date: 2014-05-18
forum: General Help
---

### Post by nstgc379 on 2014-05-18
On ZFS I've read that the entire FS locks down until it can be fixed. Is this the behavior in BTRFS as well? My concern is that the checksum might be miss computed. If this were to happen recovery is, naturally, impossible, and in the case of ZFS its not possible to detect that the check sum was miss computed.

I'm using non-ECC memory and looking to upgrade to a more modern FS with greater resilience, however from all the research I've done, while ZFS offers *exactly* what I want, it also seems to require that I have better equipment than I have (namely ECC memory).

---

### Post by lukeiamyourfather on 2014-06-02
It's my understanding that ECC memory is necessary for data integrity regardless of what file system is used because a bit could flip at any point, even after the data has been verified by a checksum and is being used by an application. 

What do you mean by ZFS locks down until it can be fixed? When ZFS comes across corrupted data it rebuilds it from the parity data or a mirror on the fly with little or no discernible performance impact. If it can't recover from the corruption at all then it will let you know what file is affected so the user can do whatever they want with it (continue on knowing it's corrupted or get rid of it) but everything else goes on with business as usual.

If data integrity is that important to you then look at getting a machine with ECC memory (plus a file system with checksums).

---

