---
title: "Recover LUKS partition"
date: 2018-03-11
forum: General Help
---

### Post by ndurner on 2018-03-11
Hi,

I have accidentally overwritten a LUKS partition with mkswap:
```

# mkswap /dev/sdb1
mkswap: warning: /dev/sdb1 is misaligned
mkswap: /dev/sdb1: warning: wiping old crypto_LUKS signature.
Setting up swapspace version 1, size = 1,8 TiB (2000398893056 bytes)

```

Is there a way to recover the partition?

---

### Post by #&amp;thj^% on 2018-03-11
Yikes! Well you **might** get lucky see this: [https://unix.stackexchange.com/questions/203051/recover-luks-partition-after-overwriting-first-few-bytes-of-luks-container-syst](https://unix.stackexchange.com/questions/203051/recover-luks-partition-after-overwriting-first-few-bytes-of-luks-container-syst)
Sure hope you kept Back -Ups
Good Luck!

---

