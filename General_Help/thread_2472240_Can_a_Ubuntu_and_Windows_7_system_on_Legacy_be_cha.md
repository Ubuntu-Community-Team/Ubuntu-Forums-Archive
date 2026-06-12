---
title: "Can a Ubuntu and Windows 7 system on Legacy be changed to UEFI in computer."
date: 2022-02-21
forum: General Help
---

### Post by SUPERFITTER on 2022-02-21
Can a Ubuntu and Windows 7 system on Legacy be changed to UEFI in computer.  I have a dual boot system with Windows 7 and Ubuntu and I want to go to Windows 10 which needs to be UEFI.  Can this be changed?

Thank you

---

### Post by Impavidus on 2022-02-22
I don't think Windows 10 requires UEFI, but it's recommended, in particular when dual booting. If your computer properly supports UEFI (support isn't necessarily proper support), which is not certain for computers old enough that they originally came with Windows 7, you can change to UEFI. You also have to change from MBR partitioning to GPT. I've heard that there are tools that can convert an Ubuntu system like that, but it may be better to try a fresh install. Try an Ubuntu live disk in UEFI mode, backup all data, wipe the hard drive, install Windows, install Ubuntu, restore your backups. Maybe you can take the opportunity to jump to a later Ubuntu release too.

---

