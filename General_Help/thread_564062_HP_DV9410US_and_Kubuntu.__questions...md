---
title: "HP DV9410US and Kubuntu.  questions.."
date: 2007-09-30
forum: General Help
---

### Post by c0rrupts3ct0r on 2007-09-30
I have a HP Pavilion DV9410US and i am running Kubuntu 7.04 feisty.  Sometimes when i lock the screen and walk away the PC will freeze. Is there anything i am going to have to change to make it more compatible?
Sometimes it will freeze when I shut the PC off. I haven't tried to hibernate or suspend yet. Somewhere i seen where I can disable APIC or APCI.  I have the Nvidia 6150 graphics card onboard and i had to disable LAPIC before i installed it or i would get the famous "lava lamp" effect when i get to the GUI before installing..

Can anyone suggest some changes either to the GRUB menu (command line switches) or in KDE?.. Would be much appreciated
Thanks
Christopher

---

### Post by SonjaMichelle on 2007-11-17
I have an HP ndv9410us as well. I can't get kubuntu 7.10 to even boot. I've tried both 32bit and 64 bit versions. Looking at the boot screen it seems to hang around where the hald daemon might be loading. I've had success with bot x32 and x64 on a homebrew AMD Athlon 64. But no luck on the HP, unless it's installed under vmware.

---

### Post by c0rrupts3ct0r on 2007-12-09
From what I've found I've gotten Kubuntu to boot on my laptop but after i added nolapic in the boot line in the grub menu.. seems like the 6150 geforce has to do with it.. after you install the Nvidia drivers with envy or restricted drivers make sure to take that line out or you will get "nvdia seems to be edge triggered " and X will refuse to start.. I still have some random lockups with my laptop. I went back to XP on it. runs fine with no problems. But i really would like to learn about linux and it seems to run faster than vista or XP would.. 

If you boot with nolapic on the live CD it will boot into a gui just fine.. if you dont it will do that crazy lava lamp effect and it will lock up.. all has to do with the nvidia 6150 grafix...

---

