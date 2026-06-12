---
title: "Wubi on Win8"
date: 2013-02-12
forum: General Help
---

### Post by Jimbrix on 2013-02-12
Hello!

I'm going to install Windows 8 and I would like to know if Wubi is fully compatible with it.

I have a ASUS N55SL.


Thank you.

---

### Post by oldfred on 2013-02-13
The issue is more with new computers and Windows 8 on how Windows 8 is installed. Windows 8 pre-installed always uses UEFI and gpt partitioning.

Wubi does not work with gpt partitioning.

But if you install Windows 8 in BIOS/MBR mode it should work.

       Wubi does not work on gpt partitioned drives or Window 8 that is pre-installed.
[http://ubuntuforums.org/showpost.php?p=12399988&postcount=2](http://ubuntuforums.org/showpost.php?p=12399988&postcount=2)
Grub4dos (which wubi uses) doesn't work with GPT disks (required by UEFI)

---

