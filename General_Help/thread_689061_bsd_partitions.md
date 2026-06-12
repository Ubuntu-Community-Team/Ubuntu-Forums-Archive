---
title: "bsd partitions"
date: 2008-02-06
forum: General Help
---

### Post by bgruber on 2008-02-06
Using Gutsy, I find that I cannot mount my UFS bsd partitions because they are not showing up in /dev, though they do show up in dmesg:
```
$ dmesg|grep bsd
[   20.806972]  sda1: <bsd: sda7 sda8 sda9 sda10 sda11 >
$ ls /dev/sda*
/dev/sda  /dev/sda1  /dev/sda3  /dev/sda4  /dev/sda5  /dev/sda6
$ 

```

I know this used to work, though I don't really know when (may have been in Feisty, then again, maybe not).

Anybody?

---

### Post by bgruber on 2008-02-06
i rebooted my computer for some other reason and now this works. oh well.

thanks anyhow.

---

