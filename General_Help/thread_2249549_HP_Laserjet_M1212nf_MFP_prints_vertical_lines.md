---
title: "HP Laserjet M1212nf MFP prints vertical lines"
date: 2014-10-23
forum: General Help
---

### Post by TI9 on 2014-10-23
Help Anyone

I'm using HP Laserjet M1212nf MFP printer. I change the toner cartridge, no problem after that. Didn't use the printer for awhile, then went to try it, and the top inch would print, but below that is just greyed out, with vertical lines, unreadable. 

So I printed a "test page," from the PC, and no problem, it printed just fine. Then tried a "self test configuration," from the printer, and again, no problem. Both printed clear, readable and aligned.

Any ideas what or where the problem is?

Thanks for your help.

---

### Post by JazzPotato on 2014-10-23
What program are you printing from and what file type is it? Have you tried printing anything else, or anything using another program? Perhaps it is a software problem.

---

### Post by tgalati4 on 2014-10-23
Could be a network connection problem.  Try unplugging the network connection a few times to clean the connection.  Check the connection at the router end.  Could be a RAM problem.  Try pulling the RAM and reseating.  Try printing a small text file, then a PDF file.  Check /var/log/cups for CUPS server errors.

If everything checks out and you are still having problems, try deleting the printer and adding a new printer.  Try adding the printer through CUPs and add another one using HP's installation program (*hp-toolbox*) and see if there are differences.

---

### Post by TI9 on 2014-10-30
Thanks, for the help, I trying to clean the connection, no change, just made it worse. Cannot print (PDF, PNG, JPG), but txt docs worked ok before. Not I'll try to delete and add the printer, and see if it works,

Thanks again

---

