---
title: "lpr: The printer or class was not found"
date: 2007-02-26
forum: General Help
---

### Post by 999alfred on 2007-02-26
While I am new to Unbuntu I have been running Slackware for quite a while. I decided to give Ubuntu a try, but I have run into a problem. 
I have installed CUPS and configured my printer and can print a test page, but when I try to use any command line command, lpr lpq, etc, I get an errors as follows.

$ lpr <filename>
lpr: Error - no default destination available.

$ lpr -P1440 menu.lst
lpr: The printer or class was not found.

$ lpadmin -d 1440
lpadmin: The printer or class was not found.

Printer is verified by both CUPS, [http://localhost:631](http://localhost:631) and the gnome printers util.

So, why is my printer not recognized by command line input?

tj

---

### Post by bill-linux on 2007-03-01
I had a great deal of trouble with LPR at first. I had installed the "lpr" packaged. The correct package to install is cupsys-bsd -- this contains the bsd lpr commands (lpr, lpq, etc) configurated for use with cups. Are you using cups and do you have cupsys-bsd installed?

---

### Post by windwalker78 on 2007-08-27
> **999alfred said:**
> While I am new to Unbuntu I have been running Slackware for quite a while. I decided to give Ubuntu a try, but I have run into a problem. 
I have installed CUPS and configured my printer and can print a test page, but when I try to use any command line command, lpr lpq, etc, I get an errors as follows.

$ lpr <filename>
lpr: Error - no default destination available.

$ lpr -P1440 menu.lst
lpr: The printer or class was not found.

$ lpadmin -d 1440
lpadmin: The printer or class was not found.

Printer is verified by both CUPS, [http://localhost:631](http://localhost:631) and the gnome printers util.

So, why is my printer not recognized by command line input?

tj

I know this is stupid but here is how I solved the problem:

#apt-get install lpr  (thought the command is part of the standard ubutu install it installed again and removed the current Window Managers + cupsys-bsd :confused:)
#apt-get install kubuntu-desktop cupsys-bsd

Now your lpr command will work as intended.

---

