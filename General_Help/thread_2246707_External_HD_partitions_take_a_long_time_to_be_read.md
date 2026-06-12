---
title: "External HD partitions take a long time to be ready."
date: 2014-10-02
forum: General Help
---

### Post by Robbyx on 2014-10-02
The delay on mounting the External HD  only happens on a cold restart,  and sometimes the partitions  are never ready, but if I restart the operating system  the external HD will get mounted without much delay.

This is from my fstab relating to the external HD:

#/dev/sdd1: 
UUID=13AC-9C9E /media/xhd_vfat vfat relatime 0 0
#/dev/sdd2:
UUID=23fcb4e3-c94e-44de-b7a9-105da58918c6  /media/xhd_system_data ext4 relatime 0 0
#/dev/sdd3: 
UUID=c99be12f-3a2d-4411-ab7c-5696167482dc /media/xhd_old_bacs ext4 relatime 0 0
# /dev/sdd4
UUID=84a9cb0b-6006-4996-8b4a-2edc07cc25c4 /media/spare4 ext4 relatime 0 0
 
Any ideas to help the boot up past the mounting of the external HD?

Robin

---

