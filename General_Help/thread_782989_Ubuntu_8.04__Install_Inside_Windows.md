---
title: "Ubuntu 8.04 : Install Inside Windows"
date: 2008-05-05
forum: General Help
---

### Post by Paris Heng on 2008-05-05
Dear,

I just downloaded Ubuntu 8.04. I mount the .iso in Windows XP, what i found out is, it can straight to install in the** C/:** drive!!!! 

Can somebody tell how is the installation would be? It is like sort of virtual machine? If it install in C:/ (NTFS), then how this can happen? Since Ubuntu need ext file system.

Please somebody explain.

Regards

---

### Post by jimv on 2008-05-05
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by cdenley on 2008-05-05
I think it basically modifies the windows boot to optionally boot into a livecd environment saved in your windows install. I think it supports persistent changes to the filesystem, though. It is physically stored in your windows filesystem, but doesn't run alongside windows, so no virtualization.

---

### Post by Paris Heng on 2008-05-06
> **cdenley said:**
> I think it basically modifies the windows boot to optionally boot into a livecd environment saved in your windows install. I think it supports persistent changes to the filesystem, though. It is physically stored in your windows filesystem, but doesn't run alongside windows, so no virtualization.

1. So, what is the different if in straight installed in Windows and I install using virtual machine (VMware)? Same right? Because VMware also creating a folder in the NTFS file system.

2. What does it mean by [COLOR="Red"]no virtualization[/COLOR]?

---

### Post by cdenley on 2008-05-06
The ubuntu filesystem is stored in an image on your ntfs partition, as if it were a virtual disk for a virtual machine. However, when you boot to it, the entire computer is handed over to ubuntu, and you are not running windows. If you were to use a virtual machine, all your system resources would be split between the virtual machine and real machine, and the virtual machine would run as an application within your real machine. You can use both simultaneously, and the two can interact with each other as if they were two networked computers. With the wubi install, after you select between windows or ubuntu at the boot menu, you only have one usable operating system.

---

