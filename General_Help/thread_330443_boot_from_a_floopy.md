---
title: "boot from a floopy"
date: 2007-01-03
forum: General Help
---

### Post by avantgardaclue on 2007-01-03
"Hi guys/gals

My PC has 2 hard disks, HDA is windoze and HDB is linux/ubuntu 6.06

Over the christmas break decided to reload windoze. That actually went surprisingly well, lost no documents and now have a relatively nice windows system (mainly for the wife's benefit!)

In doing so i have lost my GRUB boot loader. Turn the puter on and straight into windows it goes. NOT what i want or need!"

.... This is from another thread i posted half an hour ago, and after a lot of faffing about i came up with the idea of booting from a floppy. I am a bit confused by what i find on the internet so can anyone come up with the precise instructions how to make a boot flooppy for me?

BTW my ubie is on HDB1 [apparently] if this helps.

I will then archive my docs/pics and  reinstall ubie. Is it worth installing 5.10 or should i stay with 6.06?

many thanx

---

### Post by Sef on 2007-01-03
Read [Recovering GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") after installing Windows.

or 

Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

What has happened it that Windows thinks it is the only operating system.   One of those two will get GRUB back.

---

### Post by avantgardaclue on 2007-01-03
Did the trick with the Ubuntu live cd, grub seamed happy, rebooted and........ nothing, still goes straight to windows.

Guess I'll have to do a partial reinstall to get GRUB installed.

Hey ho, thanks for the help!

---

