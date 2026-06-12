---
title: "Sound problem [15.04]"
date: 2015-09-12
forum: General Help
---

### Post by Hal_Hal_ on 2015-09-12
Hi,

I have no sound , with this card on ubuntu 15.04 : 
```
$ lspci|grep Audio

Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
```

Can you help me ?
PC:Sound works with windows .

---

### Post by dino99 on 2015-09-12
check your bios/uefi is set to 'hda', not ac97
check the plugged jack(s): strict same color
install paref & pavucontrol to fine tune if neccessary; but a reboot should set it automaticaly
run 'journalctl' to know about possible warnings (bright white lines) and errors (red lines) (lightdm/pam errors can be ignored, as well as 'pcc not found')

---

### Post by Hal_Hal_ on 2015-09-12
I checked everything but nothing happens.

---

