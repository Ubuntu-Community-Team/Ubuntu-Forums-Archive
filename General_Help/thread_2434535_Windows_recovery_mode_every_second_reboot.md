---
title: "Windows recovery mode every second reboot?"
date: 2020-01-07
forum: General Help
---

### Post by ZarathustraDK on 2020-01-07
So I'm back to Ubuntu again (a couple of years) after quite a Windows-hiatus due to my old rigs Samsung 960 pro SSD not wanting to play ball.
I installed 19.10 with the "Erase everything"-option on my primary nvme (where Windows used to reside), everything went well.
Now though, every time I reboot from a working session the pc starts up windows recovery mode, I then pick "boot with other device", choose "ubuntu", pc restarts, and I get to the Grub-menu where I can choose to boot into Ubuntu. It does this _every_ time I've been booted into Ubuntu on a prior run.

Is it some Grub-related thing I can change/delete? It's not a show-stopper, just immensely annoying.

---

### Post by CelticWarrior on 2020-01-07
It looks like you have a UEFI system that still has an entry for the Windows previously installed.

Please open the firmware settings, Boot menu, and change the first bootloader to Ubuntu. The remaining and now useless Windows entry can be dealt with after assuring the Ubuntu is booting as it should be.

---

### Post by ZarathustraDK on 2020-01-07
Great, that was it thank you. Thought that entry had been fried with the fresh Ubuntu-install and that it was some weird grub-behavior picking up on some windows-leftovers.

---

### Post by CelticWarrior on 2020-01-07
The installer usually don't delete old .efi files in the ESP.

---

