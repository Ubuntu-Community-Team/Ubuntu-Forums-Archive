---
title: "Printing questions"
date: 2007-12-09
forum: General Help
---

### Post by BradNeuman on 2007-12-09
Short/easy version of question:

In KDE there was an "add special/pseudo printer" option, which seems to be gone now that I am using GNOME. When I try to actually print something I see print to file and print to PDF options, but in the printers dialog there seems to be no way to add a pseudo printer. I am using gusty btw.

Long version:

Here is why I want a pseudo printer. I am trying to get a public workstation to print to the campus LPD queue. I can add a printer which will successfully print to the network printer, except I want to be able to change the username, hopefully in a pop-up dialog. The idea is that users will select the printer, then get a pop-up asking for their username, then print to lpd://username@printerser. I think if i had a pseudo printer i could edit the /etc/cups/printers.conf file to fix this. lpadmin doesn't seem to actually change anything. There may also be a way to do it with foomatic, but so far I haven't had any luck.

thanks,
Brad

---

