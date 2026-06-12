---
title: "[SOLVED] Ubuntu 8.04 on Windows XP - error during installation"
date: 2008-05-20
forum: General Help
---

### Post by khamanpl on 2008-05-20
Hallo,

I tried to install 8.04 on Windows XP through Wubi. After chosing Ubuntu from Grub I get the message (messages are translated):

[B]Checking installation...
Partitioning with Guide[/B]
and error:
[B]Main file system not defined.
Please correct it in partition menu.[/B]

I can only click OK (witch does nothing but reapearance of error) and hard reset of the computer. Nothing else can be open.

---

### Post by ago on 2008-05-20
Try to uninstall, run chkdsk /r from within windows on the target partition, then run wubi again

---

### Post by khamanpl on 2008-05-21
Helped. Problem was with some error on one partition. Thanks.

---

