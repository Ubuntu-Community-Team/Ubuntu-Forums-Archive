---
title: "Migrating a ZFS pool to another computer + adding some tricks"
date: 2019-11-25
forum: General Help
---

### Post by uhmka on 2019-11-25
Hi, I have two machines with ZFS pools in raid5(#II 18TB) and raid6(#I 12TB). Both are ~3 years old. And #1 is snapshot and send to #2 each night.
So far so good.

Now #1 is full and the disks are meanwhile very old. So I tried to migrate #2 on a new raid5 pool, which is in a JPOD 4-disk case, connected via USB3.0(=#3 20TB)
Several things went wrong with send and receive. 
- The copy on #3 needs much more space ?!? ~10-30%
- The copytime is incredible slow over USB3.0, approx. 30-50MB, while #1 and #2 should be 10x faster. 

Additional some questions arose:
- While copying, can I compress to a stronger level (time doesn't matter here that much), while new data in future is only compressed in LZ4?
- Can I deduplicate once the archived data, while working without deduplication for the future (for performance reasons)?
- Can I remove some extreme large files (virtual machines > 100GB) from some older snapshots?

How can I guarantee, that #3 is recognized in computer2, after replacing the old disks. 

Both machines run Ubuntu 16.04.

Best regards and thanks, 
Uwe

---

