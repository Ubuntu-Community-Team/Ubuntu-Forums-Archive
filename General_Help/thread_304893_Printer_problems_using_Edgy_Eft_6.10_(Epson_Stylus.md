---
title: "Printer problems using Edgy Eft 6.10 (Epson Stylus 740)"
date: 2006-11-22
forum: General Help
---

### Post by jsstevenson on 2006-11-22
Hello...

Having installed Edgy Eft 6.10 it seems I can no longer print!

I am using an Epson Sylus Color 740 connected using USB.

The printer works and this has been confirmed by booting into XP.

The odd thing is that if I use the CUPS frontend ([http://localhost:631/printers/EPSON_Stylus_COLOR_740_USB_1](http://localhost:631/printers/EPSON_Stylus_COLOR_740_USB_1)) and I select "Print Test Page" the printer works immediately and successfully and prints a test page.  If I select "Print self-test page" then the printer does what it does with any other type of file - it doesn't print!!!

I have considered it might be related to permissions but would welcome any thoughts or suggestions on how to resolve this issue.

I have attached a printout of the CUPS frontend that shows an unsuccessful job just sitting 'there'!  It is simply listed as "stopped".

Thanks in advance for any thoughts.

Jamie.

---

### Post by jsstevenson on 2006-11-25
Any thoughts????!!!!

---

### Post by Voxxi on 2006-11-25
I've had the same problem, except with a different printer (Canon MP500). I just got it working today. What I did was change the printer driver in CUPS to a different one. The one supplied for my printer didn't work, it printed, but it printed an A4 page on a A5 area. 

Anyway, how to change your driver:

1) Go into the "Printers" dialog for CUPS.

2) Right click on the printer and hit properties.

3) Go into "Drivers".

4) Select a printer from the list. It should change the driver for your printer.

5) Attempt to print a page using OpenOffice or gEdit.

6) If it doesn't work, select another printer.

I'm sorry I can't offer a better solution, but something is better than nothing at all ;) .

---

### Post by jsstevenson on 2006-11-25
Thank you for your reply... the odd thing is that I have already tried this without success, however having given it another go after reading your post, the printer now seems to be printing - odd, but good.

Thanks again.

---

### Post by drobvice on 2006-12-04
I have a similar issue.  I don't have an Epson Printer but I have an MP500 and using Edgy.  I installed the drivers for my printer listed in this thread... [http://www.ubuntuforums.org/showthread.php?t=282096](http://www.ubuntuforums.org/showthread.php?t=282096) and I used the web interface to set it up.  I printed a test page, and printed a page in firefox and the results were gorgeous!  Something happened when I rebooted and could not print a thing.  I have messed and messed with it and can't fix it.  I am thinking it has something to do with the newer version of CUPS.  Maybe using the web interface does something to permissions. I was starting to believe this is the case, based on the fact that error_log in /var/log/cups mentioned "unauthorized" alot.  I've filed a bug report but no responses of any value so far.

---

