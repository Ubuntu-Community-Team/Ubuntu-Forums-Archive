---
title: "Grub does not show my second hard drive"
date: 2016-03-07
forum: General Help
---

### Post by SUPERFITTER on 2016-03-07
My second hard drive does not show up in the grub menu.  It contains another two operating systems.   Is there a way to add it to the Grub Menu?

---

### Post by yancek on 2016-03-07
The first thing to try if you have Ubuntu or one of its derivatives installed on the first drive is to run:  sudo update-grub from a terminal.  Watch the output to see if your other systems are detected.  If they are, you should be good.  If they are not, google "boot repair ubuntu" and go to the site and download the boot repair software and run it selecting the option to Create BootInfo Summary and post the link here.

You should indicate which system is your primary and it would be helpful if you also posted what systems you have on the external drive.

---

### Post by SUPERFITTER on 2016-03-09
Thank you yancek

I tried the   sudo update-grub, without success. I found this site: [FONT=times new roman]
[/FONT]**[SIZE=3]Reinstall / Recover GRUB from Ubuntu live CD / USB[/SIZE]**

[http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

Worked great, I have three Linux and one Windows 7 operating systems and they all show up on Grub>

---

