---
title: "Unable to change what to boot into"
date: 2014-12-19
forum: General Help
---

### Post by lolerzone on 2014-12-19
I normally don't use anything but ubuntu, but today I had a reason to boot into windows 7. As i use ubuntu the most, I obviously have the primary OS set to ubuntu. When I tried to boot to windows,my keyborad did not work. I tried using a PS/2 keyborad too, but that still did not work.

Any ideas?

---

### Post by Gordonbp531 on 2014-12-19
Do you mean that the keyboard didn't work *after *you booted into Windows 7, or before?

---

### Post by lolerzone on 2014-12-19
in the boot screen i could not select what OS i wanted, and thus it just boots into ubuntu

---

### Post by Gordonbp531 on 2014-12-19
But the keyboard works perfectly OK when you are booted into Ubuntu?

---

### Post by lolerzone on 2014-12-19
yes

---

### Post by Gordonbp531 on 2014-12-19
What happens if you boot up into a Live CD/USB?
What type and make of computer?

---

### Post by oldfred on 2014-12-19
Also do you have settings in BIOS to enable USB ports or specifically enable USB keyboard or mouse.
Both Ubuntu & Windows seem to have drivers that ignore BIOS for USB keyboards. But grub does not add drivers for that and just relies on BIOS setting. And any BIOS update resets BIOS back to defaults.
With my system I had to turn on USB keyboard & mouse after every BIOS update.

---

