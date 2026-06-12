---
title: "False Partition Usage Data"
date: 2013-07-09
forum: General Help
---

### Post by AcFreeman on 2013-07-09
I'm trying to resize my main HDD partition in Ubuntu 13.04 in order to make a smaller partition to install Windows on. Going into my home folder properties, it says I have over 650 GB of free space left, which sounds about right:[INDENT][ATTACH=CONFIG]244543[/ATTACH][/INDENT]
However, in GParted, it says that the partition is completely full, and thus won't allow me to resize it:[INDENT][ATTACH=CONFIG]244544[/ATTACH]
Does anyone know how to fix this error??[/INDENT]

---

### Post by oldfred on 2013-07-09
Only the newest version of gparted works with LVM. I do not know LVM and it used to be you could not use gparted at all with LVM. You are only seeing the LVM partition not each mapper partition inside the LVM.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

---

### Post by Cheesemill on 2013-07-10
Can you post the output of the following commands so we can see how you have LVM set up.
```
sudo pvs
sudo vgs
sudo lvs
ls -l /dev/mapper
df -h
```

---

### Post by Cheesemill on 2013-07-10
Can you post the output of the following commands so we can see how you have LVM set up.
[CODE]sudo pvs
sudo vgs
sudo lvs
ls -l /dev/mapper
df -h[CODE]

---

