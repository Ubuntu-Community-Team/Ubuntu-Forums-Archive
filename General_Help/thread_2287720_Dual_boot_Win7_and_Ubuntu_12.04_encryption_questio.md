---
title: "Dual boot Win7 and Ubuntu 12.04 encryption question - ecryptfs and bitlocker"
date: 2015-07-21
forum: General Help
---

### Post by ilicpro on 2015-07-21
Hi,

I have Windows 7 and Ubuntu 12.04 installed on my computer, and I would like to encrypt both operating systems. I have these partitions:

- system reserved NTFS
- windows 7 main partition (C:\) NTFS
- auxiliary partition NTFS
- main ubuntu partition ext4
- linux swap

I was wondering if it would be a good idea to use encryptfs to encrypt my home folder in ubuntu (I have only 1 user account), and then use BitLocker in order to encrypt my Windows C:\ partition? Is it feasible, or it could mess up something? I would leave my auxiliary NTFS partition unencrypted, and I don't have need to access my C:\ partition from Ubuntu and vice versa.

Thanks

---

### Post by oldfred on 2015-07-21
Booting may be an issue.
I do not know encryption, but one user had encrypted Windows which has a proprietary MBR, not standard Windows. And then you cannot install grub to MBR, nor let it.
But some users have been able to just install grub to the MBR of a flash drive and use that to boot. Flash drive can still be used for data as MBR is just for Booting.

---

### Post by ilicpro on 2015-07-22
Would encrypting only my home directory in Ubuntu with encryptfs, and not encrypting Windows at all, cause any issues or it should be just fine?

---

### Post by oldfred on 2015-07-22
I believe that works as the only difference is a pass phase to unencrypt /home (and swap) when you boot. 
But I have not used encryption except keypassX for passwords.

But with any encryption, really good backup procedures are required. There is no way to recover some data if some types of corruption or forgetting pass phase.

---

