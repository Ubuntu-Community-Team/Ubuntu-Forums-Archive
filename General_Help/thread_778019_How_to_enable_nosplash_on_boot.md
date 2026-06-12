---
title: "How to enable nosplash on boot"
date: 2008-05-01
forum: General Help
---

### Post by Venom_Man on 2008-05-01
I currently have two main partitions on my drive one with fiesty and the other with hardy. i installed the hardy partition with an alternative cd  and when i go to boot it i get past the second stage boot strap then i see loading in the top left then it freeze right when the splash screen should appear. my question is how do i change it so that it will boot up and load with no splash just like using a live cd. any help would be great

---

### Post by scragar on 2008-05-01
you'd have to edit grub, find out which partition has grub on, then mount it if need be, and navigate to ```
/boot/grub/menu.lst
```and edit it, find the boot line for whicher OS isn't booting, and remove the notes "quite" and "nosplash" in the line starting "kernel" under the right section, save and reboot.

---

### Post by Venom_Man on 2008-05-01
where do i edit the grub is it at boot or in terminal

---

### Post by scragar on 2008-05-01
from boot will only let you edit it on a 1 go basis(changes are lost between boots).

from a terminal use```
gksudo gedit
```to edit it in the text editor.

---

### Post by Venom_Man on 2008-05-01
i dont have a grub folder on any of my hda partitons if it matters i am on a ppc.

---

### Post by -Zeus- on 2008-05-01
> **Venom_Man said:**
> i dont have a grub folder on any of my hda partitons if it matters i am on a ppc.

it's /boot/grub

---

### Post by Venom_Man on 2008-05-01
> **-Zeus- said:**
> it's /boot/grub
thats what i meant, sorry if it was confusing, i was looking in my boot folder and there was no grub folder within it. all i had was a bunch of other text files

---

### Post by scragar on 2008-05-02
then it would be stored on your second partition, mount it. that's not hard from hardy(go Places>Computer and just double click the partition), same fiole path applies, except now your proberly going to have to use ctrl+L to find mount path and use that first:```
sudo gedit **/media/disk**/boot/grub/menu.lst
```where the bold bit is the path.

---

