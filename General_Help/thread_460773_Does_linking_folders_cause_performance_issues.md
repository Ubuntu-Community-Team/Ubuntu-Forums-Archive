---
title: "Does linking folders cause performance issues?"
date: 2007-06-01
forum: General Help
---

### Post by ineluki12 on 2007-06-01
Hello,
I'm wondering if soft-linking a folder that's normally in one place to another location can cause a degradation in performance. For example, if I perform the following, is it going to hurt my performance (assuming equal performance from different disks):

```

cp -RPv ~/.wine /media/nvraid
ln -s /media/nvraid/.wine ~/.wine

```
Or
```

cp -RPv ~/.VirtualBox /media/nvraid
ln -s /media/nvraid/.VirtualBox ~/.VirtualBox

```

Thanks!

---

### Post by dave-5B on 2007-06-01
changed my post...

---

### Post by dave-5B on 2007-06-01
i use a similar setup, mounting a directory from my fileserver in mnt then linking to it in home directory, works fine, but network bandwidth is the limiting factor for me

i really think this problem would have been solved at some point and dont think it would be an issue

maybe you could do some test to find out?

---

