---
title: "dpkg-reconfigure  command"
date: 2013-04-12
forum: General Help
---

### Post by sgm277 on 2013-04-12
Hi All,

How can I know which applications can be reconfigured by dpkg-reconfigure?  Eg, dpkg-reconfigure tzdata is used to adjust the timezone. how to list others ?

Thanks,

---

### Post by steeldriver on 2013-04-12
Try

```
sudo debconf-show --listowners
```

---

### Post by sgm277 on 2013-04-21
Thank you very much stelldriver !!!  That is what I want !!!

---

