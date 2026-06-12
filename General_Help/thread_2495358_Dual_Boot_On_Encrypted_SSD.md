---
title: "Dual Boot On Encrypted SSD"
date: 2024-02-15
forum: General Help
---

### Post by mikegreen8 on 2024-02-15
Hi.
I have an encrypted laptop with Windows 11 pro. I want to turn this into a dual boot windows/ubuntu, and the ubuntu partition should be encrypted with the windows bit locker. Is this possible ?

I think the first steps would be:
1. Shrink the Windows partition
2. Make an ext4 partition
3. Boot Live ubuntu 22.ISO USB and install ubuntu onto the ext4 partition

How can I make the ubuntu partition encypted with Windows Bit Locker ?

Thanks,
M...

---

### Post by grahammechanical on 2024-02-15
I think that the correct policy is to use Windows tools with Windows partitions and Linux tools with Linux partitions. And always defrag the Windows partition before making any changes and make sure Windows still boots.

Regards

---

### Post by hrsetrdr on 2024-02-15
The Ubuntu installer Ubiquity will give you options for creating an encrypted partition.

---

