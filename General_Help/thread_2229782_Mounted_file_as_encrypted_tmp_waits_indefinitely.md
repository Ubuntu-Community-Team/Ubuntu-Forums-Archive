---
title: "Mounted file as encrypted /tmp waits indefinitely"
date: 2014-06-15
forum: General Help
---

### Post by temmokan on 2014-06-15
I am using encrypted swap file and /tmp, both are mounted from files. OS: Ubuntu 12.04 x86_64.

In /etc/crypttab:

```
cswap           /var/swapfile          /dev/urandom    swap
ctmp            /var/tmpfile           /dev/urandom    precheck=/bin/true,tmp,size=256,hash=sha256,cipher=aes-cbc-essiv:sha256
```

In /etc/fstab

```
/dev/mapper/cswap                         none           swap    sw              0       0
/dev/mapper/ctmp                          /tmp           ext2    defaults,nodev,noexec,nosuid 0 0
```


FIlesystem where both files are located is mounted first in /etc/fstab. 

What I observe:

1. Encrypted swap file is always mounted without problems
2. /tmp in, roughly speaking, 50% of case waits for mounting indefinitely (no amount of waiting helps).
3. If OS is restarted (Ctrl-Alt-Del) on the above waiting phase, both encrypted files are mounted normally without extra waiting.
4. If I try to use partitions instead of files to mount, no such problem ever occurs (checked on another Ubuntu installation).

I would prefer to handle that without hassle of shrinking existing volume(s) and creating separate partitions for swap and /tmp.

I have found no useful clues in syslog/dmesg/whatever. Looks like the reason is quite simple, I would appreciate any clue on how to determine it.

Thanks.

---

