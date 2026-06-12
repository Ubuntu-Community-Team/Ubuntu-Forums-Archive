---
title: "Nvidia help"
date: 2006-11-28
forum: General Help
---

### Post by cmmike1 on 2006-11-28
Recently I bought a NVidia GeForce FX5200. Before i put it in my computer i installed the nvidia drivers and added them to the xorg. I backed up my xorg before doing this. Then I put the card in my computer and now Ubuntu Dapper hangs up on loading hardware drivers everytime. The card works perfectly in windows but i can't seem to get it to work in Ubuntu. I would like to get this problem fixed as soon as possible and have the new card up and running in ubuntu. If anyone can help please let me know.

---

### Post by taurus on 2006-11-28
You need to reconfigure your X now since you replaced your graphic card.  Boot into recovery mode from GRUB menu and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```

---

### Post by cmmike1 on 2006-11-28
I can't get ubuntu started at all with the card in the computer. This happens with the livecd also. It always stops at loading hardware drivers. Should i try downloading the edgy live cd and see if that works? I'm fairly new to ubuntu and don't really know much about it but i would love to figure this out with someones help.

---

### Post by taurus on 2006-11-28
So, you replaced your old video card with the new nvidia card and now your machine won't boot at all, not even with the recovery mode!!!

---

### Post by cmmike1 on 2006-11-28
it won't boot into any version of ubuntu. it hangs up on the loading hardware drivers. The video card i was using at first was and onboard one by intel. When i remove the nvidia one it will boot up but since i changed the xorg before hand it gives me errors. I'm going to see if a new install of edgy will do the trick but if not i have no idea as to what the problem could be.

---

### Post by taurus on 2006-11-28
If it's an onboard, then you need to go into the BIOS and disable it.

---

### Post by cmmike1 on 2006-11-29
how would i do that. I have an HP Pavilion desktop.

---

### Post by taurus on 2006-11-29
When you first turn on your computer, press either <Esc>, Del, F2, or even F12 to get into your BIOS.  Please consult the manual for your computer to learn exactly which key you have to press and how to disable something in the BIOS.  If you make a wrong choice while you're in the BIOS, you may not be able to even boot your machine.

---

### Post by cmmike1 on 2006-11-29
alright. I'll look in the manual. Thank you for everything you have told me.

---

### Post by cmmike1 on 2006-11-29
nothing seems to work. In my bios it has my video card set as PCI but ubuntu stalls at loading hardware still. even on the live cds too. I'm not sure what to do now. If you need me to take picture I can try and maybe then you will have a better understanding of the situation.

---

### Post by feest on 2006-11-29
put back your previous vga card, enter the line put in the new one apt-get nvidia-glx and that other code to activate the driver (look it op should be on the forums) , should work

---

### Post by cmmike1 on 2006-11-30
i will try that soon. If it doesn't work i'm lost.

---

### Post by cmmike1 on 2006-11-30
I have found a guide that has my exact problem at [http://doc.gwos.org/index.php/Nvidia_Intel_Integrated]("http://doc.gwos.org/index.php/Nvidia_Intel_Integrated") but the page never loads for me. Does anyone have this guide saved anywhere because maybe it will help. this was the original guide I used that didn't work [https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28nvidia%29]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28nvidia%29")

---

