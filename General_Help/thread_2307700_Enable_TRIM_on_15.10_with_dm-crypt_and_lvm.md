---
title: "Enable TRIM on 15.10 with dm-crypt and lvm"
date: 2015-12-27
forum: General Help
---

### Post by xquercus on 2015-12-27
I did an install of xubuntu 15.10 on my OCZ vertex 4.  I enabled encryption and lvm using the default installer partitioning scheme.  Is trim enabled by default in this case?  I verified that the default fstrim job is installed in /etc/cron.weekly.  Also...

issue_discards is enabled in /etc/lvm/lvm.conf

```
issue_discards = 1
```

dmsetup shows the allow_discards flag so I guess dm-crypt is dealing with trim properly.

```
root@vader:/# dmsetup table /dev/mapper/sda5_crypt
0 499611648 crypt aes-xts-plain64 00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000 0 8:5 4096 1 allow_discards
```

A manual trim seems to show success.

```
root@vader:/etc/cron.weekly# fstrim -a -v
/boot: 179.7 MiB (188361728 bytes) trimmed
/: 226.6 GiB (243305496576 bytes) trimmed

```

So what's the verdict?  I haven't changed anything from default.  Is trim really enabled by default and functioning on my machine?  Is there any way I can be sure?

---

