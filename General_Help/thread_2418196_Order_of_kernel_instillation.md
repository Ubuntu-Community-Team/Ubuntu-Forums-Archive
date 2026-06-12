---
title: "Order of kernel instillation"
date: 2019-05-03
forum: General Help
---

### Post by chefmike07 on 2019-05-03
What is the order for installing the kernel? 

1. linux-headers-5.0.11-050011_5.0.11-050011.201905020559_all.deb
2. linux-headers-5.0.11-050011-generic_5.0.11-050011.201905020559_amd64.deb
3.linux-image-unsigned-5.0.11-050011-generic_5.0.11-050011.201905020559_amd64.deb
4.linux-modules-5.0.11-050011-generic_5.0.11-050011.201905020559_amd64.deb

Is this my understanding of the installation of the kernel without the lowlatency files?


linux-headers-5.0.11-050011_5.0.11-050011.201905020559_all.deb
  linux-headers-5.0.11-050011-generic_5.0.11-050011.201905020559_amd64.deb
  linux-headers-5.0.11-050011-lowlatency_5.0.11-050011.201905020559_amd64.deb
  linux-image-unsigned-5.0.11-050011-generic_5.0.11-050011.201905020559_amd64.deb
  linux-image-unsigned-5.0.11-050011-lowlatency_5.0.11-050011.201905020559_amd64.deb
  linux-modules-5.0.11-050011-generic_5.0.11-050011.201905020559_amd64.deb
  linux-modules-5.0.11-050011-lowlatency_5.0.11-050011.201905020559_amd64.deb

---

### Post by victor.pont on 2019-05-03
A simple > dpkg -i linux-headers-*.deb linux-image-*.deb linux-modules-* should work.
Regards.

---

### Post by monkeybrain20122 on 2019-05-04
Just put them all in one folder, say ker, then  do

```
cd /path/to/ker

sudo  dpkg -i *.deb
```

It will figure out the order itself.
Make sure there is no error message, then reboot.

---

