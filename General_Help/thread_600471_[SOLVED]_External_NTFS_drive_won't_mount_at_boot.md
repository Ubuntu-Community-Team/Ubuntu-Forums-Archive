---
title: "[SOLVED] External NTFS drive won't mount at boot"
date: 2007-11-02
forum: General Help
---

### Post by FuturePilot on 2007-11-02
I converted my external FAT32 drive to NTFS. Problem is, now it won't mount at boot. It did when it was FAT32, but now it won't. I have to manually mount it now. Is there anyway to get it to mount automatically at boot like it did before?

---

### Post by Pumalite on 2007-11-02
Are you talking at boot of the computer?. Then check your /etc/fstab
(an external drive should be 'hot' regardless of the format)

---

### Post by FuturePilot on 2007-11-02
> **Pumalite said:**
> Are you talking at boot of the computer?. Then check your /etc/fstab
(an external drive should be 'hot' regardless of the format)
Yes, I mean when booting the computer.

It actually does mount at boot, but it takes about 15 seconds to mount after I login. Is that normal? When it was FAT32 it showed up immediately. I installed ntfs-config and enabled writing to external drives. I'm not sure if that's what did it or not. So it seems to be working now.

---

### Post by ddrichardson on 2007-11-02
> **FuturePilot said:**
> I installed ntfs-config and enabled writing to external drives. I'm not sure if that's what did it or not. So it seems to be working now.That may be the problem as ntfs is supported on 7.10.

---

