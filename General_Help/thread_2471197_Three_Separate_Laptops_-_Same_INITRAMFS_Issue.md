---
title: "Three Separate Laptops - Same INITRAMFS Issue"
date: 2022-01-23
forum: General Help
---

### Post by swormuth2 on 2022-01-23
Good day,

Perhaps someone can steer me in the right direction here...

I made the switch from Linux Mint to Ubuntu-MATE because I find it much lighter on resources for older hardware.  So far I have installed it on three separate laptops of various ages, the "youngest" being about three years old.  They are all installed the same way, and they all experience the same odd behavior.

I chose to use encrypted ZFS with no other partitioning other than what the Ubuntu installer sets up by default using the full disk.  At random, all three will drop to an INITRAMFS prompt when booting, just before the encryption unlock prompt.  I don't have to do anything else other than CTRL-ALT-DEL and the next boot works fine most times.  Sometimes I need to do it twice and it boots.  Most times it boots fine on the first shot.  

What on earth could be going on here?  They never failed with Mint, so I can't imagine three separate laptops would have the exact same type of hardware issues?  It must be a bug, but the "Report A Bug" option in Ubuntu just takes me to a page telling me how to report a good bug.  It's not very helpful.

Any thoughts would be appreciated.

---

### Post by oldfred on 2022-01-23
Do not know zfs, but some discussion of issues and need to houseclean old snapshots manually.
[https://ubuntuforums.org/showthread.php?t=2465671](https://ubuntuforums.org/showthread.php?t=2465671)

---

