---
title: "I don't understand the disk space"
date: 2019-04-09
forum: General Help
---

### Post by panja on 2019-04-09
I have Ubuntu 18.04.2 server running and when I do a ***df -h*** command I get the following:
```

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       219G  6.5G  201G   4% /

```

To me that doesn't make sense.
The size of the disk is 219GB, 6,5GB is used but I only have 201GB available.
If I add 201GB + 6,5GB I have 208GB (rounded). Where is the other 11GB?

---

### Post by Impavidus on 2019-04-09
5% is reserved space for privileged processes. This is to ensure that you have enough overhead room to fix your system when an unprivileged user fills up the filesystem and to prevent fragmentation.

---

### Post by panja on 2019-04-09
Ahhh I see.
Indeed 5% of the 219Gb is roughly 11GB which I 'lost'.

Thanks!

---

### Post by SeijiSensei on 2019-04-09
The 5% figure dates back to a time when drives were orders of magnitude smaller than they are today. It's possible to set the reserved space to a smaller value when formatting a drive with mkfs.

```
sudo mkfs -t ext4 -m 2 [device]
```

would reserve 2% rather than the default 5%. The tunefs command allows you to change the amount of reserved space on an existing ext filesystem with the same -m parameter.

---

