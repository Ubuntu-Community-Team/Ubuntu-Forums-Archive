---
title: "urgent problem with mbr, please help"
date: 2007-07-02
forum: General Help
---

### Post by xubu_caapn on 2007-07-02
okay,
on my dad's computer, i installed xubuntu on an external hdd. it installed grub, obviously, overwriting the windows boot loader. so i needed the external hdd to boot the computer into windows. now, his motherboard got fried. we replaced it, but when i turned on the external hdd and tried to boot, nothing happens. i got a grub error. so i plugged in the external drive into my laptop, deleted EVERYTHING, hoping that i could run fixmbr or something from that...?
so, i can't boot into windows cuz there isn't a bootloader. is it possible to install one to the external hdd? please respond soon, this is my dad's computer, not mine :(

---

### Post by splintercellguy on 2007-07-02
Try Super GRUB? [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by xubu_caapn on 2007-07-02
thank you for the suggestion. i tried it, selected fix windows boot, and i am now able to boot into windows, but once there i can't move my mouse or use my keyboard. they are both plugged into the new motherboard -- does anyone know if that's the cause? and if so a possible solution? i already tried different usb ports etc

---

### Post by CrispyFried on 2007-07-02
windows generally doesnt like being transplanted to new motherboards.. is it **exactly** the same kind of motherboard?

are the usb ports enabled in the bios? I assume the keyboard works till it hits windows? do you have access to a ps/2 mouse or keyboard?

---

