---
title: "After updating 12.10 to 13.04 no boot?"
date: 2013-04-29
forum: General Help
---

### Post by scythe000 on 2013-04-29
I get to grub, but when i tell it to boot, i just have the "Ubuntu" screen with the progress bar that goes forever. Rebooted multiple times. let sit overnight, etc. Same issue. Help!

---

### Post by grahammechanical on 2013-04-29
Standard actions whatever the Ubuntu version apply.

Recovery Mode>Resume. You get that as the second option under the Advance Options for Ubuntu sub-menu at the Grub menu. Be aware the Recovery mode resume laods Ubuntu without a video driver. You may not get Nouveau but llvmpipe so the user experience will not be fantasic but from a desktop you can activate a video driver in System Settings>Software & Updates>Additional Drivers tab. You will have to experiment to find which one of the drivers offered works for your machine.

You can also at the Grub menu select Ubuntu and press E. That will put Grub into Edit mode. Look in the boot parameters for the line that has > initrd.lz quiet splash and change it to > initrd.lz nomodset quiet splash Press f10 to boot. Be aware that the system will load with llvmpipe.

Regards.

---

### Post by scythe000 on 2013-04-29
> **grahammechanical said:**
> Standard actions whatever the Ubuntu version apply.

Recovery Mode>Resume. You get that as the second option under the Advance Options for Ubuntu sub-menu at the Grub menu. Be aware the Recovery mode resume laods Ubuntu without a video driver. You may not get Nouveau but llvmpipe so the user experience will not be fantastic but from a desktop you can activate a video driver in System Settings>Software & Updates>Additional Drivers tab. You will have to experiment to find which one of the drivers offered works for your machine.

You can also at the Grub menu select Ubuntu and press E. That will put Grub into Edit mode. Look in the boot parameters for the line that has  and change it to  Press f10 to boot. Be aware that the system will load with llvmpipe.

Regards.

Thanks for the quick reply!

So, that works. I can log in under recovery>resume. Upon reboot, it does the same thing. Do I understand that I have to replace my video driver before i reboot?

---

### Post by cariboo on 2013-04-29
Moved to General Help, as Raring has been released, and this sub-forum is now focusing on Saucy.

---

### Post by scythe000 on 2013-04-30
If it helps, I'm using an integrated Intel video card, so no 3rd party drivers. According to my research, I'm using the latest one.

---

