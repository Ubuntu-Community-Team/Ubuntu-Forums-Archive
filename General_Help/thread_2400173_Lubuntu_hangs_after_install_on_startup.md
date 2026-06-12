---
title: "Lubuntu hangs after install on startup"
date: 2018-09-03
forum: General Help
---

### Post by starwars-geek98 on 2018-09-03
Hello everyone,

I just installed Lubuntu 32bit to an old (2009) Sony Vaio netbook that previously had Windows 10 though it was slow. So, I thought that Lubuntu would be one of the better options.

Booting and installing from a USB drive went well and here I was for my first boot. I ejected the USB and started it (I actually tapped the restart option in the install wizard but forgot the USB so it booted up to the install again, so I had to power it off and try again), when it arricved at the standard ubuntu-ish loading screen, it just went to sleep like I had told it to... The LED (for the HDD) was blinking like it was at sleep mode, so I tapped the power button and brought it up again. It loaded and went to the log-in screen. Before I was able to type my password the laptop went to sleep again and the same happened, it would hang and I wasn't able to go to the desktop. One time I managed to type the password and tap Log-in but the same happened.

I don't have a clue of the cause actually, does anyone here have an idea and a fix possibly for this? 

**P.S** Lubuntu ran well in the testing mode before you choose to install and the netbook meets the requirements so I do not think that computer power is the problem. More over, Windows never had the same issue (7,8.1,10).

Thanks in advance.

---

### Post by sgian on 2018-09-04
Have you tried booting into recovery mode?  [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)  Then you can try looking in the syslog for errors if it boots properly in Recovery mode.

Which version of Lubuntu are you using?  16.04? 18.04?  If 18.04 and you can't figure out why it won't work right, try 16.04 with the 4.4 kernel.

---

### Post by starwars-geek98 on 2018-09-04
Thanks for answering!

I'm using Lubuntu 18.04, I forgot to mention.

I will give it a try thanks for the tip!

Also, the problem dissapears when I enter the desktop, so all in all the problem occurs in the log-in screen and the loading screen at system boot.

---

### Post by starwars-geek98 on 2018-09-05
So, I took a look in the syslog but didn't find anything related to the problem...

---

