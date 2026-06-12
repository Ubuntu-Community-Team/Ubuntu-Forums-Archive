---
title: "Install HPLIP on Lubuntu 12.10"
date: 2012-11-11
forum: General Help
---

### Post by Rex Bouwense on 2012-11-11
I installed Lubuntu 12.10 on my ASUS EeePC 1000h last month.  To print a document I downloaded the latest HPLIP version (3.12.10a).  In the lxterminal I entered the following commands:

```
rex@rex-1000H:~$ cd Downloads
rex@rex-1000H:~/Downloads$ sh hplip-3.12.10a.run
```

and received the following response:

```
Creating directory hplip-3.12.10a
Verifying archive integrity... All good.
Uncompressing HPLIP 3.12.10a Self Extracting Archive.

HP Linux Imaging and Printing System (ver. 3.12.10a)
HPLIP Installer ver. 5.1

Copyright (c) 2001-14 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Sun-11-Nov-2012_10:41:27.log

warning: CUPSEXT could not be loaded. Please check HPLIP installation.
```

Now what?

---

### Post by gordintoronto on 2012-11-11
For a couple of years now, I have never had to mess around with printer drivers. I run printers, or maybe printer or printing, I click on Add, I select (in my case) network printer, a couple of seconds later my printer appears, and I click on it and say "OK" however many times it is required.

Or perhaps you need to read this page:
[http://www.cyberciti.biz/faq/debian-ubuntu-hp-linux-imaging-printing-warning-cupsext/](http://www.cyberciti.biz/faq/debian-ubuntu-hp-linux-imaging-printing-warning-cupsext/)

---

### Post by Rex Bouwense on 2012-11-12
Thank you for the web site.  After digging deeper, it appears that HPLIP 3.12.10a does not support Ubuntu/Lubuntu 12.10 and the new version of HPLIP (3.12.11 I think) is not due for release for a couple of weeks.  I guess I must wait.  Fortunately, I am dual booting with Lubuntu 12.04 on this machine and it has HPLIP installed and working properly.  Thanks again.

---

### Post by Rex Bouwense on 2012-11-27
HP has released HPLIP 3.12.11 and I installed it.  That solved the problem.

---

