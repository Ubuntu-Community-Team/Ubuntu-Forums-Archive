---
title: "Boots straight into Ubuntu"
date: 2016-07-20
forum: General Help
---

### Post by infpython on 2016-07-20
Hello Ubuntu Forums I am having trouble with grub so basically I have two Linux operating systems and instead of taking me to the grub menu it just boots straight into Ubuntu, I have corrected a problem like this in the past but I just can't remember. *Thanks!* 

(_Yes I have tried Google_)

---

### Post by Dennis N on 2016-07-20
Are these two OSes both installed in BIOS mode (no UEFI)? If so, boot into Ubuntu, then run **sudo update-grub** in the terminal. Reboot, and see if the other OS now shows in your grub menu.

---

### Post by infpython on 2016-07-21
I installed both from the BIOS. Even if it finds no other OS's shouldn't still prompt me with a grub menu ?

(trying to update grub now)

Edit: It found linux image, initrd image, memtest86+ but not my other linux OS or Windows (Dual boot) didn't work still boots straight into Ubuntu.

---

### Post by infpython on 2016-07-21
If I reinstall my other Linux OS is it possible it will work?

---

### Post by oldfred on 2016-07-21
May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

