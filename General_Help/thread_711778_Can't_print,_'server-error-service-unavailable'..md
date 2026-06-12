---
title: "Can't print, 'server-error-service-unavailable'."
date: 2008-03-01
forum: General Help
---

### Post by vanhelmont on 2008-03-01
My HP Laserjet 1100 used to work, then I started getting an error message:

   CUPS server error

   There was an error during the CUPS operation: 'server-error-service-unavailable'.

and it won't print.  I can delete the printer, then the printer configuration tool can automatically detect the printer, so I'm guessing there is no hardware problem.  

If I run 
root@capybara:~# ps -ef | grep cups
I get
root      5250     1  0 Feb23 ?        00:00:00 /usr/sbin/cupsd
as well as several lines that I think are print jobs.

When I tried
root@capybara:~# netstat -l | grep cups
I get
unix  2      [ ACC ]     STREAM     LISTENING     48960    /var/run/cups/cups.sock

I also did this

root@capybara:~# /etc/init.d/cupsys stop
 * Stopping Common Unix Printing System: cupsd                           [ OK ] 
root@capybara:~# /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd                           [ OK ] 

and nothing seems to help,
Thanks for any suggestions.

---

### Post by richbl on 2008-06-25
Is your printer networked or local?

If networked and running samba, some recent updates (avahi possibly) caused me to have to reinstall samba entirely. Turns out that without smbclient and/or smbfs, you'll generate the CUPS error you've indicated when attempting to print to a networked printer.

I just now ran into this problem, and re-installation worked in my case.

Good luck.

---

