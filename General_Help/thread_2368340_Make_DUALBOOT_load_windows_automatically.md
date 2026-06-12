---
title: "Make DUALBOOT load windows automatically"
date: 2017-08-09
forum: General Help
---

### Post by warmango on 2017-08-09
As the title suggests, how do i make a Ubuntu/Win10 dualboot automatically load windows? i got this to work once and then i had to hold shift to boot to Ubuntu, and that was with win7, so how do i do that?

---

### Post by oldfred on 2017-08-09
Is this a new UEFI system or is Windows 10 from an upgrade of an older Windows with BIOS boot?

If UEFI, you can just go into UEFI and set Windows as first in boot order. 
And then when you want Ubuntu use UEFI one time boot menu key, often f10 or f12 but check your manual for correct key(s).

If UEFI, from Ubuntu you can see boot order, and most systems will retain a change using efibootmgr.
sudo efibootmgr -v

See also 
man efibootmgr

       Change boot order with efibootmgr, some require all 4 hex char others 1 is ok.
sudo efibootmgr -o 2,1

---

