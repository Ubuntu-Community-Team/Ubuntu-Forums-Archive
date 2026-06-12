---
title: "Kernel Panic - not syncing"
date: 2007-04-09
forum: General Help
---

### Post by GuitarHero on 2007-04-09
Runing edgy.  

I turned off my computer the other day, today I turn it on and i get this error:
Kernel Panic - not syncing: No init found.  Try passing init= option to kernel.

It wont move past this, and I can't even boot a live cd.  I don't even know how to troubleshoot this without a terminal.  I searched and found similiar but not exact problems to mine and the fixes dont work because i cant get to a terminal.  When I try to boot a live cd, it says:
request_module: runaway loop modprobe binfmt-0000 
fives times then does nothing.

help

---

### Post by GuitarHero on 2007-04-09
bump

---

### Post by pointone on 2007-04-10
Have you tried booting using the recovery mode option in GRUB?

Have you tried more than one live CD? Or at least downloading and burning the Ubuntu CD again? If every live CD is failing, this would generally indicate a hardware problem.

---

### Post by GuitarHero on 2007-04-10
Ive tried multiple authentic shipit cds to no avail.  Recovery mode does not work either.  When i try to boot to my vista hard drive it says there was a change in hardware or something and can not boot.  But i havnt changed any hardware recently so i dont know whats happening...

---

### Post by pointone on 2007-04-10
I recommend trying a barebones boot: remove any unnecessary hardware from your system and try booting. If it works, add hardware back piece by piece until you find the one causing the problems. By remove any unnecessary hardware, I mean boot with only the CPU, one stick of RAM, the video card, and one hard drive.

If even this barebones setup fails, try running Memtest86 (I think it's included on the Ubuntu CD... but it's been a while since I actually checked.)

---

### Post by GuitarHero on 2007-04-10
I tried that and it turns out it was a stick of ram causing the problems.  It seems to me that grub or ubuntu should tell me its a hardware or even specifically a ram problem and not give me the vague Kernel Panic message.  Oh well.  

Thanks a lot.

---

