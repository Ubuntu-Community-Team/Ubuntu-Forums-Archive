---
title: "Grub deleted after installing Windows 10"
date: 2016-01-02
forum: General Help
---

### Post by Kuhkaefer on 2016-01-02
I had lubuntu and Windows xp on my laptop. After eventually replacing xp with windows 10, I couldnt boot Lubuntu anymore. 
With Super Grub2 Disk I could finally boot it with a disk.
How can I reinstall grub now so that I dont need the disk anymore?
I tried it with sudo grub-install but it failed because it couldnt find the installation device.
Under /boot I found the grub file but efi was missing
Can anyone help me?

---

### Post by Kuhkaefer on 2016-01-02
Problem solved!
I found boot-Repair, which easily fixed everything:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ajgreeny on 2016-01-02
Please mark as SOLVED from the "Thread Tools" menu at the top

---

### Post by timotheus3 on 2016-01-14
im fairly sure any upgrade/install of windows alongside ubuntu installs the windows bootloader, so you cant access grub

---

