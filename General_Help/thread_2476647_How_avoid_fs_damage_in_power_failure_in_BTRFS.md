---
title: "How avoid fs damage in power failure in BTRFS ?"
date: 2022-07-01
forum: General Help
---

### Post by aug7744 on 2022-07-01
Hello.
Thanks for reading my topic.
I use OS for an long time and never had used an fs almost impossible to fix as BTRFS.

Had happened an power failure and the fs was unmounted.
doing
sudo btrfs check --readonly --force --mode original --progress /dev/sda3

Opening filesystem to check...
parent transid verify failed on 6888587264 wanted 124745 found 121965
parent transid verify failed on 6888587264 wanted 124745 found 121965
parent transid verify failed on 6888587264 wanted 124745 found 121965
Ignoring transid failure
ERROR: could not setup extent tree
ERROR: cannot open file systems

Not is possible mount that fs.
Another fs (ntfs, exfat, fat32 and possibly ext2-3) when happen power failure the fs not is damaged at point not being recovered, but looks BTRFS not has any protection when happen partial written in power failure.
Another fs are possible mount and fix.
An average user not will mount that BTRFS fs damaged.

How configure BTRFS to avoid that type of problem ?
Where to contact BTRFS devs to say about it ?

Have an good night.

---

