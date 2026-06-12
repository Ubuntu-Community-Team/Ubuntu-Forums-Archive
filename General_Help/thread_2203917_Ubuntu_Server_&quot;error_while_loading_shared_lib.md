---
title: "Ubuntu Server &quot;error while loading shared libaries&quot;"
date: 2014-02-05
forum: General Help
---

### Post by Arachan on 2014-02-05
Hello,

I'm currently booted to a live usb on my ubuntu server. I did something stupid (I think I broke a lib symlink or something, not sure :roll:) and it stopped booting, get a kernel panic. 

When I try to chroot in I get the following error:

```
/bin/bash: error while loading shared libaries: libc.so.6: cannot open shared object file: No such file or directory
```

Can someone please point out how to fix this? I can give any info needed if you tell me how :)

Cheers.

---

### Post by Arachan on 2014-02-15
bump

---

### Post by ubudog on 2014-02-15
Hi,

Try running:
```
ldconfig
```

---

### Post by Arachan on 2014-02-16
Hello,

I can't boot so I ran it while booted to the live USB.

```
ldconfig
/sbin/ldconfig.real: Can't create temporary cache file /etc/ld.so.cache~: Permission denied
sudo ldconfig

```

Which returns an empty terminal. What should I do?

Thanks for the help.

---

### Post by Arachan on 2014-02-21
Anyone got any tips?

---

