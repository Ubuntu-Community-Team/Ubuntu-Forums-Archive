---
title: "Fresh install with btrfs, full encryption"
date: 2017-11-12
forum: General Help
---

### Post by chronos00 on 2017-11-12
Is there any simple way to reuse the standard Ubuntu installer, using the option to just format everything and encrypt the while disk, and then reinstalling and manually choosing BTRFS?

---

### Post by wildmanne39 on 2017-11-12
Moved here since this is not about 18.04.

---

### Post by chronos00 on 2017-11-13
Thank you Wild manne.

To answer my own question, in the hope to help others, this is the best solution I found so far, and worked flawlessly:
[https://albertodonato.net/blog/posts/full-disk-encryption-with-btrfs-on-ubuntu-xenial.html](https://albertodonato.net/blog/posts/full-disk-encryption-with-btrfs-on-ubuntu-xenial.html)

I got fresh Ubuntu install, LUKS and LVM2 container, BTRFS filesystem, 2 subvolumes (root and home), and working encrypted SWAP.

With those instructions, even hibernation works!

---

