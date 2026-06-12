---
title: "Problems booting Windows"
date: 2008-05-11
forum: General Help
---

### Post by thezood on 2008-05-11
I have a dual boot system with Windows on sda1 and Ubuntu on sda2. After upgrading to Hardy (by complete format), I have been unable to boot Windows. It starts to boot but a few seconds into the boot process, the computer just reboots. Same thing with failsafe mode. The Windows bootloader works - otherwise, I wouldn't get the Windows failsafe menu.

I actually had another problem first; I installed Hardy which worked fine, but after rebooting once, I couldn't boot either Windows or Ubuntu. GRUB just said "Error 17". So I reinstalled Hardy, which solved that problem. But now, a week later, I've realised I can't boot to Windows.

I've gathered that quite a few people have similar problems but I'd really like to solve this without having to reinstall Windows and kill all my programs. Does anyone have any ideas? 


Thanks in advance,
anders.

---

### Post by mikazo on 2008-05-11
I think I had a similar problem once when I was reinstalling Ubuntu on its own partition and I had Vista Home Premium on the other partition. After trying to boot into Windows several times, I eventually somehow gained access to the recovery console or something. I did some kind of startup repair and it fixed everything.

This may help but I don't know what version of Windows you are running. [http://www.tipandtrick.net/2008/how-to-open-windows-vista-recovery-environment-re-console-from-installation-cd/]("http://www.tipandtrick.net/2008/how-to-open-windows-vista-recovery-environment-re-console-from-installation-cd/")

---

### Post by pro003 on 2008-05-11
you should have first fix your windows boot problem then reinstall ubuntu...


you could do that by simply repairing your windows installation and after that carefully install ubuntu...

---

### Post by thezood on 2008-05-12
Yes, repair Windows, then reinstall GRUB. I wasn't aware there was a "Repair" installation method. :) Thanks.

---

