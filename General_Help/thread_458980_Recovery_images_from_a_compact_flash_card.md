---
title: "Recovery images from a compact flash card"
date: 2007-05-30
forum: General Help
---

### Post by Trosky on 2007-05-30
Hi, I am trying to recovery a compact flash memory card, but my ubuntu cann't recognise, when i try to mount the device, the system show this message: "It is not possible to mount the device. Possible there is not anything in the unit"

Googling a little, I tryied to mount the device in sda3 (I did also with sda1 and sda2, both were busy) and appear the following error:

user@user-desktop:~$ sudo mount /dev/sda3 /media/camara/ -t vfat
mount: kind of incorrect file system, incorrect option,
       incorrect superblock in /dev/sda3, there is not the code page, 
       or any other error
      (¿Aren't you try to mount an extended partition,
      instead of any logic partition which is inside?
      In some cases there is information in syslog, try
   dmesg @tail or something similar

user@user-desktop:~$ dmesg | tail
[34581.755132] sdb: Unit Not Ready, sense:
[34581.755142] : Current: sense key: Medium Error
[34581.755146]     Additional sense: Cannot read medium - unknown format
[34582.070914] sdb : READ CAPACITY failed.
[34582.070917] sdb : status=1, message=00, host=0, driver=08 
[34582.070925] sd: Current: sense key: Medium Error
[34582.070929]     Additional sense: Cannot read medium - unknown format
[34582.078355] sdb: Write Protect is off
[34582.078365] sdb: Mode Sense: 04 00 00 00
[34582.078368] sdb: assuming drive cache: write through

Any orientation for solving the problem?

Thanks

---

### Post by Trosky on 2007-05-31
Any idea for solving this?

---

### Post by LaRoza on 2007-05-31
I have two questions:

1. Could Ubuntu read this card before?
2. What happened between then and now?

---

### Post by Trosky on 2007-06-02
No, it is not recognised before by linux.

Some time ago, I connected this card in a windows xp system and it broke. I couldn't access again to this card.

---

