---
title: "slow HDD file transfer speeds"
date: 2008-03-27
forum: General Help
---

### Post by Patto77 on 2008-03-27
When transferring files from one hard drive to another, or even to the same hard drive, I'm getting a real slow transfer rate of about 4-6 mbps.  Under Vista, I usually get between 25-40mbps going from one drive to another and it's almost instant when moving a file on the same HD.  Have I forgotten to tick a 'transfer faster' button somewhere?

I'm using Kubuntu 3.5.8

Any ideas as to why the transfer rate is so slow?

---

### Post by dcstar on 2008-03-27
> **Patto77 said:**
> When transferring files from one hard drive to another, or even to the same hard drive, I'm getting a real slow transfer rate of about 4-6 mbps.  Under Vista, I usually get between 25-40mbps going from one drive to another and it's almost instant when moving a file on the same HD.  Have I forgotten to tick a 'transfer faster' button somewhere?

I'm using Kubuntu 3.5.8

Any ideas as to why the transfer rate is so slow?

```
man hdparm
```

---

### Post by tgalati4 on 2008-03-28
Are you transfering between NTFS and EXT3?  Transfers between NTFS file systems is pretty fast.  Transfers between EXT2/3 file systems is also pretty fast.  Transfers between them may not be.

---

