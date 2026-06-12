---
title: "Can't boot after RAM upgrade =/"
date: 2007-01-05
forum: General Help
---

### Post by mo79 on 2007-01-05
I have 2 HD's, the first an 80GB which has Ubuntu 6.06 and the second a 60GB slave with Windows XP. 

I setup dual booting by temporarily disconnecting my XP drive (formerly master) during the installation of Ubuntu and then after re-assigning the XP drive as slave, creating a manual GRUB entry in the master Ubuntu so I can boot to XP when needed, making it think it's master at those times.

All has been well for ages, but today on my Dell Dimension 4550 I added another 512MB RAM to total 1GB (I put the new, Crucial, module in the slot where the existing one was and the old one in the second slot - just as I had initial probs figuring fitting).

On first boot after installation I was prompted to confirm the new memory, which I did, and then when GRUB appeared, booted into XP. All fine, the My Computer properties showed the change - and the boot time was much better too. I also let Windows then take charge of virtual memory as it was stock set at 768MB.

Anyway, after a reboot - and with design to go into Ubuntu, I found I can't boot! I just get 2 options to press a key to retry or enter the setup utility. I retried a few times/repowered but to no avail. So then I went into the BIOS utility and all seems fine but the 80GB drive now shows up as XXXX TB (terrabyte?) rather than GB. And the drive (a Seagate I bought a few months back) name has 10 exclamation marks after it. The 60G XP drive seems fine, but as I haven't re-opened comp yet I can't boot back into XP as you can only boot from the primary hard drive from Dell's boot choices screen.

I'm petrified of putting XP back as master yet in case the same thing happens, and I don't know how bad this prob is. Please fire my suggestions my way, thanks!

---

### Post by teaker1s on 2007-01-05
could it be in need of a bios update?

---

### Post by joneberger on 2007-01-05
what happens if you remove the RAM?  can you boot now?

---

### Post by mo79 on 2007-01-05
Something freaky just happened...I just turned the comp on again and it's all okay (well I didn't load into Ubuntu, but I'm sure it would've worked)... Hmm, I dunno what's happening. I'm gonna see if it's just to do with rebooting tomorrow, or maybe I just had a weird one-off digital poltergeist! For now I just want to work with XP tonight. But please stay tuned to this thread people in case I come crying back from my laptop. :-?

---

### Post by luvinit on 2007-01-06
Weirdness surrounding ram adding is not unusual. If you alter the ram on my gigabyte board you get allsorts of thing happening like refusing to boot, it not being recognised. If you keep swapping things around and restarting eventually it works ok.

---

### Post by mo79 on 2007-01-06
It's a weird prob. It seems if I boot into Windows then select 'restart' after some work, I then get taken to a black screen with the text 'Strike F1 to retry to reboot, F2 for setup utility'. Neither option works, but if I just turn the computer off for half an hour and then on again it's okay. I'd love to know what's going on here. :-k

---

