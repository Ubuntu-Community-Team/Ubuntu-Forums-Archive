---
title: "Installed ubuntu, want to setup grub to work with vista"
date: 2008-05-14
forum: General Help
---

### Post by agm_ultimatex on 2008-05-14
I have vista home premium 64gb on my 500 gb hard drive. I installed the unbuntu 64 bit on my slave drive. Could someone help me with setting up the grub so I can choose which OS to boot from? For me to boot into ubuntu, i must hit esc to get into the boot menu, then i select hard disks, and select my slave. I then see the grub loader, and I select ubuntu from there. (vista is also viewable from the grub there)

---

### Post by kirios on 2008-05-14
Not quite sure I understand your question. If you can already select Ubuntu or Vista in grub, what sort of help do you need?
> **agm_ultimatex said:**
> Could someone help me with setting up the grub so I can choose which OS to boot from? For me to boot into ubuntu, i must hit esc to get into the boot menu, then i select hard disks, and select my slave. I then see the grub loader, and I select ubuntu from there. (vista is also viewable from the grub there)

EDIT: Is grub installed on master or slave? Could you post your /boot/grub/menu.lst file?

---

### Post by 505 on 2008-05-14
The choice between vista and ubuntu should always come up, even if you don't select the boot device.

---

### Post by jbaileypro on 2008-05-14
My server machine which has grub boot on it,  automatically recognized both server 2003 and 2008.

---

### Post by meierfra. on 2008-05-14
Deleted, Misunderstood your problem.

---

### Post by kirios on 2008-05-14
Maybe you want the boot menu to appear without having to press Esc. 

Press Alt-F2, then type **gksudo gedit /boot/grub/menu.lst** into the dialog box that appears. 

When the menu.lst file opens, look for a line that says **hiddenmenu** and change it to **#hiddenmenu**. Look for a line that says **timeout** and make sure the value is _not_ set to **0**. Save your changes and reboot.

---

### Post by meierfra. on 2008-05-14
> Maybe you want the boot menu to appear without having to press Esc.

That's what I wanted to suggest in my deleted post. But then I realized that the OP is pressing "esc" to get into the bios and temporarily change  the boot order.
There should be a way to set the bios to always boot from the slave  drive. (But the specifics depend on the bios)

---

