---
title: "PS2 connected keyboard not functioning in bootloader.."
date: 2007-05-13
forum: General Help
---

### Post by Bejron on 2007-05-13
My keyboard (standard ps2 connected) doesn't function in the bootloader for some reason.
It has worked with this hardware configuration before but I have done some complete reinstalls since then and haven't had use for a bootloader after that but now I wanted to try Wubi out but I can't.. =(

Any way to initiate the keyboard before the bootloader kicks in ??

Mind you, it's NOT a USB keyboard so it's not in the bios. I have checked all those settings already..

---

### Post by ago on 2007-05-13
If that is when you have the choice between Windows and Ubuntu, it's a windows issue (ntldr).

---

### Post by Bejron on 2007-05-13
Correct. Anyone who has enough knowledge about the dark side (aka Windows) to help me with this ?

---

### Post by Bejron on 2007-05-20
Problem solved.. 

"USB Legacy Support" support was activated in BIOS. Deactivated it and everything worked like a charm.

---

