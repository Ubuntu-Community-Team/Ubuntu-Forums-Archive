---
title: "Cannot boot into Ubuntu after Installing"
date: 2016-03-26
forum: General Help
---

### Post by chris382 on 2016-03-26
I've got an Acer 64bit running Windows 8.1 and I've just recently installed Ubuntu on a separate partition from windows so i could dual boot. After installation, I restarted the computer and it boots automatically into Windows and I've tried entering the BIOS to change Boot order and used f12 to see if it was listed but its not there. I don't see anything that has to with Ubuntu. I have Ubuntu installed(32.6GB) with Swap (2.38GB) however i can't seem to boot into the Grub Menu to boot Ubuntu that's already installed on my computer. How can i solve this issue? I'd really like to start dual booting, thanks.

---

### Post by Rocky_Bennett on 2016-03-26
You can run boot repair from a live Ubuntu disc. I use my boot repair disc and it fixes the problem every time;

[https://sourceforge.net/projects/boot-repair-cd/](https://sourceforge.net/projects/boot-repair-cd/)

---

### Post by kc1di on 2016-03-26
If you run boot-repair and it does not fix the problem, Make sure you save the web page address it gives at the end of the run
so you can post the output here.  It may have very important information that may help us determine the problem.
My guess is that windows and ubuntu are not both installed in UEFI mode. 
Good luck.

---

