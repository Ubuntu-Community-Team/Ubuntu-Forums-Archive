---
title: "Broken lib system - need repair help"
date: 2013-02-26
forum: General Help
---

### Post by MK567 on 2013-02-26
Hello

Somehow my library system got broken in Ubuntu Raring (/lib64 and /lib).

Now I have **segfault** just after init **in ld-2.17.so**.
```
*init*[1]: Segfault at 1c ip in ld-2.17.so [7f90f094d000+23000]
```[B]

Chroot[/B] gives me segmentation fault. I can not chroot that partition.
```

# chroot /mnt
Segmentation fault (core dumped)
```
**Dpkg** does not let me reinstall libc6 into the partition when using root option.
```

sudo dpkg --root=/mnt -i /var/cache/apt/archives/libc6_2.17-0ubuntu4_amd64.deb 
dpkg: warning: subprocess old pre-removal script was killed by signal (Segmentation fault), core dumped

```No success with: [COLOR=#000000][FONT=Arial]sudo apt-get -o Dir=/mnt -V --reinstall install libc6[/FONT][/COLOR]

Some ideas?
How to understatnd that segmentation fault and how to avoid it.

---

### Post by MK567 on 2013-03-05
I don't know what exactly fixed it but i did these things:

Deleted **ld.so.cache** cache from **/etc**.
Copied** /lib/x86_64-linux-gnu** folder from live disc with same Ubuntu version.
Used **/lib64** from live cd.

After these steps i was able to chroot with command:
> **sudo chroot /mnt /bin/sh**

Downloaded libc6 with wget and installed with dpkg.

---

