---
title: "how to update bios on sony vpceb26fg i3 64bit laptop running ubuntu 16.04lts"
date: 2019-03-16
forum: General Help
---

### Post by paul_harris on 2019-03-16
i would like to see if i can update my sony with a bios with the linux system installed.
seems as tho most bios updates are for ones with windows.
is this an issue, the gpu fan seems to run full steam with video and i am interested 
to know if a bios update will fix it.

Cheers

---

### Post by oldfred on 2019-03-17
Some vendors now support updates directly from within Linux.
       [https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

I do not see Sony anywhere on lists.
If buying a new system, I would first consider vendors that support UEFI update as then they at least provide some Linux support. If you call help desk with all vendors first reponse is always, "we do not support Linux".

My motherboards have 3 ways to update UEFI - from within Windows, from a DOS bootable flash drive (FAT32), or directly from within UEFI reading a FAT32 formatted partition (I use my ESP).
Check what other options your system offers, if any, in manual or on-line.

---

