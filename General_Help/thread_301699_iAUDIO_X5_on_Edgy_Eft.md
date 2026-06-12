---
title: "iAUDIO X5 on Edgy Eft"
date: 2006-11-17
forum: General Help
---

### Post by cward002 on 2006-11-17
Hi I just purchased an iAUDIO X5. I was all excited because I have read several threads here that say it is detected very well, but when I connected it I got nothing. dmesg saw the device but and registered it as a USB Mass Storage device and said it was connected but then it unregitered it and disconnected again and I never saw any reference to it anywhere but dmesg. I have also had the problem with mounting an external hard drive. I do not currently have the output from dmesg handy but when I do I will post it. In the meantime if anyone has any ideas, it is greatly appreciated.

Colin

---

### Post by cward002 on 2006-11-23
well I tried again today and after I connected the X5 I issued an lsusb command and lo and behold the device was in the list. However, It is still not being mounted as an external USB drive nor is it seen at all in Gparted.

Thanks for any and all help

Colin

---

### Post by mlmurray on 2006-11-23
I know this isn't helpful to you, but my X5 shows up just fine.

Maybe you've got a hardware problem.  Do you have another computer you can check it with?  Can you boot another OS on your computer to see if it recognizes it?  Windows would be better to test it with, but you might try Knoppix or some other live distribution - if it works with that, then it's something in your configuration.  

If you're having problems with other USB storage devices either some driver isn't loading up right or you're USB hardware is messed up (my best guess).

---

### Post by whatintheworldisthat on 2006-11-24
I can also confirm that it works for me in edgy. I have an x5L, although I highly doubt this is making a difference.

---

### Post by cward002 on 2006-11-26
Well it is now working exactly as advertised. I was able to transfer all my music to the iAUDIO and I am listening to it as we speak. Still not sure exactly why . 

Thanks to everyone

Colin

---

