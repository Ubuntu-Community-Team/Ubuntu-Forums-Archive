---
title: "Winbind 12.04"
date: 2013-02-19
forum: General Help
---

### Post by itninjasteve on 2013-02-19
I have successfully configured winbind in 12.04 on a VM, but when I tried to install it on a physical box my permissions are screwed up.  On my home directory which is mounted using autofs from an nfs4 file server the permissions are showing nobody:nogroup

I've tried everything I could, I even rsynced the etc directory from my working VM to my non-working physical machine and ran meld on the two and saw no apparent differences.

The only difference I can see would be hardware.  Any ideas?

---

