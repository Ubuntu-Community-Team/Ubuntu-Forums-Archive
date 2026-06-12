---
title: "error when booting"
date: 2007-10-23
forum: General Help
---

### Post by rufee on 2007-10-23
i installed ubuntu 7.10 with wubi the instalation went fine but when try to boot ubuntu it gives me an error:
[B]Booting 'Ubuntu 7.10, kernel 2.6.22-14-generic'

Filesystem type is ntfs, partition type 0x7
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sdb5 loop=/ubuntu/disks/root
disk ro quiet splash automatic-ubiquity locale=en_LT

Error 17: file not found[/B]

---

### Post by ago on 2007-10-23
What version of wubi did you use? You probably have to change the (hd0,0) line to whatever is the (disk,partition) you have wubi installed on.

---

### Post by rufee on 2007-10-23
i used alpha-rev361 i think

---

### Post by ago on 2007-10-23
> **rufee said:**
> i used alpha-rev361 i think

That's an issue then

---

### Post by ClausG on 2007-10-25
I had the same problem with an older alpha, too. But with
alpha-rev368 i got it working.

Claus

---

