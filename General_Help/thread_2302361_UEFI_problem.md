---
title: "UEFI problem"
date: 2015-11-09
forum: General Help
---

### Post by atliia0014 on 2015-11-09
Hello, 
    I have installed the 14.04LTS on a new harddrive to replace a windows 8 install. I have disabled secure boot and fast boot in the bios, and I have enabled legacy boot mode. UEFI is also disabled in the boot order, and the boot order is set to the hdd first. 
    The computer is an HP E2 vision. I have read the documentation, and followed the instructions for installing on a UEFI device. As well as reading posts related to this problem. However, I get an error saying that not bootable disk has been found. I plugged the disk into another desktop to confirm that it was installed correctly. It does boot.

  Does anyone have any advice on how I can get this to work?

---

### Post by kryten35 on 2015-11-09
32 or 64 bit?  32bit is legacy only. 64bit is UEFI or Legacy.

Boot UEFI:  disable legacy   Enable secure boot
Boot Legacy:  enable legacy  Disable secure boot.

---

### Post by atliia0014 on 2015-11-09
Originally installed 32 bit. Replaced it with 64 bit. Same results.

---

### Post by kryten35 on 2015-11-09
When you press the F9 key or whatever it is on your computer,to select the disk to boot What options are you given?

Edit: Win8 does a UEFI install. Try UEFI with the 64 bit.

---

### Post by atliia0014 on 2015-11-09
Just tested it. UEFI is listed first. Then Sata. I clock sata and get the error: no boost disk has been detected or the disk has failed. 

Went back to bios. Only legacy boot sources is enabled under boot order. Secure boot configuration: legacy support enabled secure boot disabled Fast boot disabled.

Am I missing something?

---

### Post by kryten35 on 2015-11-09
Is there more than one sata entry under legacy?.Eg on my computer its sata 2 to boot my cd in legacy mode.
Edit : the ref to my dvd drive under legacy doesnt work,i have to use sata 2

---

### Post by atliia0014 on 2015-11-09
no. Only one Sata entry. I do not have any other devices connected.

---

### Post by kryten35 on 2015-11-09
Have you tried UEFI install?

---

### Post by atliia0014 on 2015-11-09
No. I read on the docs that if there is only ubuntu it is not needed. But, when I press f9 and UEFI pops up isn't that a problem?

---

### Post by kryten35 on 2015-11-09
No most people install UEFI so its easier to dual boot with Windows and because of secure boot.

---

### Post by atliia0014 on 2015-11-10
Thank you for your help. Reinstalled in UEFI mode. That works.

---

### Post by sudodus on 2015-11-10
Thanks for sharing your solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

