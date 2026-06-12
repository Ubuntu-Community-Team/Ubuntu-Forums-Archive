---
title: "Brother mfc465cn Network Printer??"
date: 2008-03-22
forum: General Help
---

### Post by teds78751 on 2008-03-22
I have install the following Brother Printer packages on my newly installed Gutsy kubuntu laptop system:

      
      brother-lpr-drivers-common
      brother-lpr-drivers-extra
      brother-cups-drivers-common
      brother-cups-drivers-extra

Each of the above packages contain "stuff" for the mfc465cn printer.  However, when I attempt to create a new printer, everything works fine up until I get to the "Select your printer from the list" part.  The mfc465cn printer is not in the list.

How do I get the printers from the above mentioned packages into the list of drivers for a new printer?

---

### Post by Shazaam on 2008-03-22
Type this in to Firefox (gets you to cups page on localhost)....
```
http://127.0.0.1:631/
```
See if your printer is there under "Manage Printers".
P.S....
Gutsy found my Brother MFC420CN by default. I did not need to add drivers.

---

### Post by teds78751 on 2008-03-22
THANK YOU VERY MUCH!! That was the avenue I was looking for.  I'm now able to print to my mfc465cn printer.  It works great!! :-D

---

