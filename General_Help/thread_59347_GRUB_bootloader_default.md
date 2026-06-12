---
title: "GRUB bootloader default??"
date: 2005-08-23
forum: General Help
---

### Post by 0vermind on 2005-08-23
I'm not sure if this is the right place for this question.

Anyways, does anyone know how to change which OS startsup by default in the GRUB boot loaded. Cause everytime I turn on my computer it says "**selected will boot in 10 seconds**" and the selected is Linux I want my Windows 2000 to be first and Linux to be the alteritive. 

Is there a way to do this or I'm I just stuck with it forever?  :-? 
[On the other hand there must be a way, somehow. With out formatting or anything]


Thanks in advance,
0vermind

---

### Post by transactionlogfiller on 2005-08-23
sudo gedit /boot/grub/menu.lst and look for the line that says "default 0"

Basically that's the number of the default os in the list, so you'll probably want to change it to 3 (recovery mode and memtest should be 1 and 2)

You can also change the timeout there.

---

