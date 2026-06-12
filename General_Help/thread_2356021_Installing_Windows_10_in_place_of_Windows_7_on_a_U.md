---
title: "Installing Windows 10 in place of Windows 7 on a Ubuntu-Windows 7 Dual Boot"
date: 2017-03-19
forum: General Help
---

### Post by madhavkode on 2017-03-19
I have a dual boot of Windows 7 Ultimate and Ubuntu 16.10 Yakkety Yak. I want to install Windows 10 in the place of Windows 7. Here's my partition info

Partition 1 : 100 GB, System NTFS (Windows 7)
Partition 2 : 50 GB, Primary ext4 (Ubuntu)
Partition 3 : 3.5 GB, Primary swap (Ubuntu Swap)
Partition 4 : 312 GB, Primary NTFS (Storage for both OS's)

I have the GRUB2 bootloader with Windows 7 chainloaded
What will happen if I directly install windows 10 from a bootable disk in the partition of Windows ?
Do I need to take any measures to secure Grub ?

---

### Post by yancek on 2017-03-19
Windows 10 has a "Custom" install option which you will need to use to select to install to the first partition where you now have windows 7.  Otherwise, windows will probably just overwrite everything.  If your windows 7 (default for windows 7) and Ubuntu are using MBR, you need to install windows 10 MBR.  Windows will overwrite the MBR on your system and you will not be asked or informed that this is being done so you will need the Ubuntu DVD/flash drive to reinstall Grub.

---

### Post by HermanAB on 2017-03-19
Why not install Virtualbox and make a Win10 VM?  That way, you will have much better control over the MS conundrum.

---

