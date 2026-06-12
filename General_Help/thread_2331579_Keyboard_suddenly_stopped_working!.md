---
title: "Keyboard suddenly stopped working!"
date: 2016-07-23
forum: General Help
---

### Post by forisonex on 2016-07-23
I have a Dell laptop and Ubuntu 16.04 installed.I was using VLC and  after some time i realised that my keyboard wasn't working for no  reason.   _i tried_ :  

Install xkbset for managing keyboard options **sudo apt-get install xkbset** Disable slow-keys **xkbset -sl** Disable accessibility so slow-keys won't turn back on [B]xkbset -a

[/B]

  and 



  Install the drivers: **sudo apt-get install xserver-xorg-input-all** If allready installed, reinstall it: **sudo apt-get --purge autoremove xserver-xorg-input-all && sudo apt-get install xserver-xorg-input-all** Reboot and try again if everything is working.


  i also updated and upgraded packages but nothing solved my problem..Please help me! i currently use onboard keyboard..

  thanks in advance guys!

---

### Post by ajgreeny on 2016-07-23
As a hardware check do you have any other OS on the laptop, eg, Windows?  Does the keyboard work using that?

If it is single boot try a live DVD/USB of a Linux OS to see if the keyboard works using that.

---

### Post by forisonex on 2016-07-24
I only use Ubuntu in my laptop..i also tried f12 on reboot but didn't work.I will try to format pc with usb keyboard!

---

