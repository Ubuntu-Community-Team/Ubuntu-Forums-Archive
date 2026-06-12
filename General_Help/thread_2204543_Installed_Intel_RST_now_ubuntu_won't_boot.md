---
title: "Installed Intel RST now ubuntu won't boot"
date: 2014-02-09
forum: General Help
---

### Post by 12padams on 2014-02-09
So I had a 3TB hard drive under windows that had endless problems with overwritting itself once I used more than 1TB of data. I gave my computer to the repair shop and they flashed my BIOS to the latest version. This didn't fix the problem and at this point both Windows and Ubuntu could still boot. He then reset the problematic 3TB drive and installed Intel RST (Rapid Storage Technology). Ever since then it appears the hard drive works fine...

I am making a youtube series called "Adventures in Arch" and recently plugged in my portable hard drive with Arch Linux installed on it ready to boot like usual. Only problem is it didn't boot. The computer just froze on the BIOS loading screen until I unplugged the portable hard drive. Then I thought "Maybe I need to fix up grub on the portable hard drive or something". So I have windows duel booted with Ubuntu and selected Ubuntu on my Windows boot manager screen like I ussually do but suddenly nup... That Ubuntu option on my windows 7 boot manager doesn't take my to grub which usually takes me to ubuntu. 

So what am I supposed to do now? I can't get grub, ubuntu or arch linux working and I've got everyone waiting on me to make my next episode.

HELP NEEDED URGENTLY!

---

### Post by david98 on 2014-02-09
Have you tried using a live boot repair disk ? [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tomlow35 on 2014-02-09
Aww, I been following your series in youtube. Been enjoying it. Have you tried disconnecting your cam and any other usb device except that external drive and keyboard and mouse? It don't sound like a bootloader issue. Have you changed anything in the bios lately?

---

### Post by oldfred on 2014-02-09
A BIOS update automatically resets everything to defaults. Perhaps you need some settings in BIOS. 
I know with my system if I update BIOS, I have to turn on USB keyboard & mouse as the default is off.

---

### Post by 12padams on 2014-02-09
Wow, I tried booting into Ubuntu again today and it works fine. Now the issue is still arch that won't boot off the portable hard drive. Ive checked the arch partitions and can browse files of the hard drive though Ubuntu so I am not sure why I can't boot arch. This is beyond you guys though right because this is arch, not Ubuntu I have the problem with now.

---

