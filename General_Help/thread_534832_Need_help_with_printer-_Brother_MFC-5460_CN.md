---
title: "Need help with printer- Brother MFC-5460 CN"
date: 2007-08-25
forum: General Help
---

### Post by Adiuvo on 2007-08-25
My dad just bought this printer, and when we connect it through USB nothing happens, no device shows up or anything. My PSP connects fine, so I'm pretty sure it's not a USB port problem or even a problem with Ubuntu.

So, I thought I'd install the drivers. I use Google and find them on the brother homepage, however when I download it they come in a 'RPM' file, which archive manager won't open. So, does anyone have any solutions?

BTW: I've tried searching and found a viable topic, however all the links were dead :(

---

### Post by linuxwizard on 2007-08-25
That printer is classified as Partially works
[http://www.openprinting.org/show_printer.cgi?recnum=Brother-MFC-5460CN](http://www.openprinting.org/show_printer.cgi?recnum=Brother-MFC-5460CN)

You should use: Drivers for Debian
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)


Howto install driver
[http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_install.html)



 Partially 
    These printers mostly don't work; you may be able to print only in black and white on a color printer, or the printouts look horrible.

---

### Post by Adiuvo on 2007-08-25
When I try that it gives me this.

[quote=Error]emiliano@family:~$ sudo dpkg -i --force-all printer.deb
Selecting previously deselected package mfc5460cnlpr.
(Reading database ... 113487 files and directories currently installed.)
Unpacking mfc5460cnlpr (from printer.deb) ...
Setting up mfc5460cnlpr (1.0.0-9) ...
mkdir: cannot create directory `/var/spool/lpd/mfc5460cn': No such file or directory
chown: cannot access `/var/spool/lpd/mfc5460cn': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc5460cn': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc5460cn': No such file or directory[/quote]

---

### Post by Adiuvo on 2007-08-25
Just logged into root and manually created the folders, then it gave me this.
[QUOTE=Stuff]root@family:/home/emiliano# dpkg -i --force-all printer.deb
(Reading database ... 113506 files and directories currently installed.)
Preparing to replace mfc5460cnlpr 1.0.0-9 (using printer.deb) ...
Unpacking replacement mfc5460cnlpr ...
Setting up mfc5460cnlpr (1.0.0-9) ...
[/QUOTE]

That's correct, right?

---

