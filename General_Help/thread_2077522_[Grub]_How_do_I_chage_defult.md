---
title: "[Grub] How do I chage defult"
date: 2012-10-28
forum: General Help
---

### Post by robtygart on 2012-10-28
I would like to change what loads first, I am playing around with another operating system but I want to make Kubuntu load by defult. 

How do I do this?

---

### Post by twipley on 2012-10-28
I cannot precise further than that, but take a look at both GRUB_DEFAULT= and GRUB_SAVEDEFAULT= over at [https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2).

EDIT: third paragraph suggests software such as "Grub customizer," which may be of help in the case of yours.

---

### Post by oldfred on 2012-10-28
You can just have the grub install in Kubuntu be the grub in charge. Then it will be first in the menu.

Boot into Kubuntu and run this.

sudo grub-install /dev/sda
sudo update-grub

---

### Post by Moose on 2012-10-28
Open the menu.lst file and cut and paste the Kubuntu entry to the top line and it should boot first..

---

### Post by robtygart on 2012-10-28
> **oldfred said:**
> You can just have the grub install in Kubuntu be the grub in charge. Then it will be first in the menu.

Boot into Kubuntu and run this.

sudo grub-install /dev/sda
sudo update-grub

Thank you that worked!

---

