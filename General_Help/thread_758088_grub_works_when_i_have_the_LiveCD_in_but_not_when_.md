---
title: "grub works when i have the LiveCD in but not when i dont"
date: 2008-04-17
forum: General Help
---

### Post by agrab0ekim on 2008-04-17
I have (after my last thread) reinstalled Ubuntu and have it up and running beside by Vista. However, when i restart my computer it tells me no boot menu found on this rom. I have my HDD boot first. So, i go into my bios and can change it so it boots from the CD and then Grub works well and i can get onto both (via the initial install screen (boot off of HDD option)) Vista and Ubuntu
how can i fix this?

---

### Post by logos34 on 2008-04-17
The first thing to try is reinstalling grub to the hard disk mbr:

sudo grub-install /dev/sda

(replace 'sda' with your HDD if different)

---

### Post by agrab0ekim on 2008-04-17
> **logos34 said:**
> The first thing to try is reinstalling grub to the hard disk mbr:

sudo grub-install /dev/sda

(replace 'sda' with your HDD if different)


how does one do that

---

### Post by agrab0ekim on 2008-04-17
fixed it:guitar:

---

