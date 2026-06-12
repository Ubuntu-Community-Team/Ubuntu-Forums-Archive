---
title: "apt-add-repository ppa:ansible/ansible"
date: 2019-02-11
forum: General Help
---

### Post by vandaanggi on 2019-02-11
```
Err:7 [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) kuberneter-xenial Release
  404  Not Found [IP: 172.217.194.102 443]
Reading package lists... Done
E: The repository 'http://apt.kubernetes.io kuberneter-xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

---

### Post by jbicha on 2019-02-11
[FONT=courier new]There's a typo in your apt line:

-kuberneter-xenial
+kubernetes-xenial[/FONT]

---

### Post by zika on 2019-02-12
xenial?
[h=1]Forum: Ubuntu Development Version[/h]

---

### Post by slickymaster on 2019-02-12
*Thread moved to **General Help**.*

---

