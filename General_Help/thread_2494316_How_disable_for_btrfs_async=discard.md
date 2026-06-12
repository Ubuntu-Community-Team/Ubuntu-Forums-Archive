---
title: "How disable for btrfs async=discard ?"
date: 2024-01-12
forum: General Help
---

### Post by aug7744 on 2024-01-12
Hello.
Thanks for reading my topic.

Kernel 6.2 has enabled async=discard for btrfs.

Simply how disable it ? Is in fstab ? what setting to add ?

Have an nice day.

---

### Post by MAFoElffen on 2024-01-12
Instead of using "discard=async" as options in the fstab, use "nodiscard"...

RE: [https://www.spinics.net/lists/linux-btrfs/msg133128.html](https://www.spinics.net/lists/linux-btrfs/msg133128.html)

---

