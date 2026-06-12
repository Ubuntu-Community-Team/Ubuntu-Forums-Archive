---
title: "Computer Dead, Need Help!"
date: 2008-01-08
forum: General Help
---

### Post by Dice836 on 2008-01-08
Hi,

Thank you in advance to anyone who can give me advice.

I installed Ubuntu on my PC, IBM net-vista.  I have been dual booting with XP and Ubuntu 7.10 for almost two weeks now.  ,The other day I had to get an update from microsoft to update XP to service pack 2.  I updated and had to restart, after restarting the computer could not read or write to my external HDD.  I restarted the computer to run Ubuntu(because Ubuntu had no problems and XP was messing up) but when the computer started, it froze on the IBM screen(First thing that comes up).  I then turned on and off the computer a couple time to see if it might reset itself.  After about 4 times powering on and off I got to a screen telling me to press F1 to continue normally or F2 to search for alternative boot-loader.  I pressed F2 and it started to search for an Operating System.  It found nothing and gave me an error with the boot-loader(said something like "none can be found").  

I mentioned this to my friend and he told me to send it in.  I do not think it is under warrenty anymore so that will not be an option, but I will call IBM and see if there is anything that they can do for me.  I wanted to ask if anyone knew if installing another boot-loader (possibly Grub?) would solve the problem.

Also does anyone know why or how this could have happened and why no OS is found?

---

### Post by p_quarles on 2008-01-08
> **Dice836 said:**
> I mentioned this to my friend and he told me to send it in.  I do not think it is under warrenty anymore so that will not be an option, but I will call IBM and see if there is anything that they can do for me.  I wanted to ask if anyone knew if installing another boot-loader (possibly Grub?) would solve the problem.
Sounds like that should do the trick. You can reinstall GRUB using the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ugm6hr on 2008-01-08
Might represent a HD problem.

Things to do:
1. Boot from a LiveCD to see if it works (it should).
2. Back up your important files from the HD using the LiveCD to an external device.
3. Boot using a HD testing disc - you can normally get one from the HD manufacturers website, or try this: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

I suspect the timing with XP SP2 update was a coincidence.

---

### Post by Dice836 on 2008-01-08
My computer freezes before even giving me a selection of an OS.  I have tried booting from the ubuntu Live CD but it does not read the CD.

---

### Post by ugm6hr on 2008-01-09
> **Dice836 said:**
> My computer freezes before even giving me a selection of an OS.  I have tried booting from the ubuntu Live CD but it does not read the CD.

Can you even enter the computer BIOS?  It's usually F12 (or F-something) on the opening screen.

---

