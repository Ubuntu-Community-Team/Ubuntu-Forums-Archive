---
title: "Broke a long working graphic driver, somehow. Cannot access Terminal in Safe Mode."
date: 2014-08-05
forum: General Help
---

### Post by Durabys on 2014-08-05
Hi.
I used the winning option in this: [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error). And it hasn't worked for me.
I have important work on the Ubuntu partition so I cannot delete it and re-install. I need help fast. The driver worked all fine till today when I installed several programs via terminal and changed font size in the Grub2 Customizer from 16 to 20.

My computer is Toshiba Qosmio x300-14y. sda has Windows 7 Home Premium 64-bit. sdb has Ubuntu 14.04 64-bit.

**SOLVED:** I am invincible! [IMG]http://ubuntuforums.org/images/smilies/guitar.gif[/IMG]  I found out the program which was causing this. Please inform people  that "Numlockx" is no longer functioning correctly for Ubuntu 14.04 and  causes a GPU corruption in the lightdm graphical manager. With the  effect of it looking like the GPU driver was the problem.

---

### Post by QIII on 2014-08-05
Hello!

Can we assume that the machine has the NVIDIA 9800M specified on their website?

Specs often change in production runs, so it is usually best to give the specifications of your particular machine rather than having people look them up.  :)

Can you also tell us exactly what you changed in the GRUB customizer and the steps you took to do that?

---

### Post by Durabys on 2014-08-05
The thing is that I just managed to get into the terminal and install an nvidia-current driver. The issue is that it does not want me leave tty1 session when going through the Ubuntu non-failsafe/non-recovery default option and when I go through the Ubuntu failsafe/recovery option and later click Resume normal boot it stops at the Ubuntu loading screen.

---

### Post by Durabys on 2014-08-05
My problem is the following: when I do ALT+CTRL+F1 on the first page with the "Low Graphics mode" after I have went with Ubuntu Generic-recovery and clicked the **failsafeX** option..it does not continue into the tty1 terminal console login but hangs/stops loading at the "**Loading extension XINERAMA**".

> **QIII said:**
> Hello!

Can we assume that the machine has the NVIDIA 9800M specified on their website?

Specs often change in production runs, so it is usually best to give the  specifications of your particular machine rather than having people  look them up.  [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

Can you also tell us exactly what you changed in the GRUB customizer and the steps you took to do that?

I changed the  font size of the boot entries text. I repeat: nothing  else caused trouble before. I had changed the sequence of entries and  added a nice picture of the Saturn V and everything worked fine till  now.

---

### Post by Durabys on 2014-08-05
I am invincible! :guitar: I found out the program which was causing this. Please inform people that "Numlockx" is no longer functioning correctly for Ubuntu 14.04 and causes a GPU corruption in the lightdm graphical manager. With the effect of it looking like the driver was the problem.

---

