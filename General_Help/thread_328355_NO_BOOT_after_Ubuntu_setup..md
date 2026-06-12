---
title: "NO BOOT after Ubuntu setup."
date: 2006-12-30
forum: General Help
---

### Post by ronkas on 2006-12-30
I had a WinXp Home sytem on my HD. Next i installed Ubuntu 6.10 with an original Live DVD.

During setup i've selected the first option for creating a partition in my current HD, when setup finished successfully, I reply "Reboot" on the popup.
Well, it rebooted, showed the GRUB loader (all OS where in the list), i've selected my fresh Ubuntu and it started. Login succesful, all where good. So I decided to reboot again to check Win integrity.

BUT NO BOOT.
No boot at all. No signal on Monitor, BIOS emit a quite long *beep*. My MoBo's diagniostic led is stuck on VGA check. (first: system boot, ok. second: CPU check, done. third: VGA check. Fourth: OS boot.)

My mobo is a DFI NF4 Ultra-D that mounts a AMD Athlon64 X2 4200+ overclocked CPU.

Ah, and HD whas finely (and freshly) defragmented two times with Evo. Diskeeper 10 utils before the setup.



Sure, not a good approch with linux, ya :S 


An other question: is my SATA-II HDD, compatibile with a P-ATA mobo?

---

### Post by bulldog on 2006-12-30
Just clock your system back to the standards,as you probably know,over clocking can damage your hardware.
If SataII is compatible with your motherboard,take a look in your documentation which came with it.

---

### Post by ronkas on 2006-12-30
thanks for reply, but sincerly, my system worked well by 2 year ago from today with only Win.
So i do not think that go back on standars can help me.
Also, i can't go in BIOS, like i said, the MoBo gives me an error on video system. (i've got one led telling me that and beeps coding)

Updates: I tried launch my Pc without any HDD connected and obiously the system stucks on the same VGA error, negating me access to the BIOS. (also no mobo brand logo is showed, repeat NO VIDEO INPUTS.)

So i guess that before worring on linux or other i must fix that damn boot error.
Suggestions? (maybe a CCMOS?)

TYIA

---

### Post by bulldog on 2006-12-30
Think a deceased graphics.

Did you turned of the power completely,also unplug it from the main and wait half an hour.
Try to boot again and if the failure persist,try another graphics.

The problem could be you over clocked your graphics as well,and ubuntu used the standard settings which unset the graphics.

---

### Post by ronkas on 2006-12-30
yeah boys, i come as a winner. :mrgreen: :mrgreen: 

I fixed it turning the BIOS in safe-mode booting useing the small jumper on my MoBo.
HD is perfect, Ubuntu and Windows too.

---

