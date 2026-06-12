---
title: "Lenovo T460S unable to update firmware"
date: 2020-12-11
forum: General Help
---

### Post by visque on 2020-12-11
I have 2 pending updates in my Ubuntu software (see attached pic)
Unfortunately nothing happens even if i did try updating via fwupdmgr.
It shows it is installed, restart the laptop and it boots right back up.
please advise if i am missing out something?

[ATTACH=CONFIG]287527[/ATTACH]

---

### Post by visque on 2020-12-12
I managed to resolved it by going thru the following steps.

BIOS/UEFI settings:
1. disabled secure boot 
2. enable legacy first
3. disabled boot order lock
4. enabled bios update without password

During startup Linux Grub menu:
1. choose recovery mode
2. enable networking
3. choose root
4. sudo fwupdmgr refresh
5. sudo fwupdmgr update

works like a charm!

---

