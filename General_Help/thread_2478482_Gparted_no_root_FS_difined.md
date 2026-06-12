---
title: "Gparted no root FS difined"
date: 2022-08-28
forum: General Help
---

### Post by sofasurfer on 2022-08-28
I'm sure this is a very simple fix but I can not find it. It doesn't always happen but then again it happens to often. In Gparted I create  a partition and format it as ext4. I go to my live dvd and click 'install' and I get error 'no root file system defined. correct this is partitioner' (or very similar wording). What am I doing wrong?

---

### Post by westie457 on 2022-08-28
This will give you some pointers.
It is mainly for dual-booting with Windows but can also be used with multiple installations.

[https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/](https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/)

---

### Post by Impavidus on 2022-08-28
In the installer, you have to select the partition where you want to install Ubuntu, then tell the installer to use it as the root partition.

---

### Post by yancek on 2022-08-28
The answer is in post 3 but I wonder why you would expect a partition managerI e to do that?  Every partition created is not going to be or the user is not going to want it to be a / (root filesystem), sometimes just a data partition.  I expect this is the primary reason, the software needs to be told what to do before it will do it and will do what you tell it to do not what you want it to do.

---

