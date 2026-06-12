---
title: "LibreOffice cannot find default printer"
date: 2019-03-17
forum: General Help
---

### Post by alansecker on 2019-03-17
I have two network printers plus cups-pdf

I set one o the network printers as the server default in  CUPS and confirmed it in:

# system-config-printer

but:

lpstat -d 

no system default destination

Which perhaps explains why LibreOffice cannot find it, or indeed display any of the printers.

Yet Firefox, Thunderbird and Abiword see all three and can print from them (!)

---

### Post by him610 on 2019-03-17
alansecker,
Sounds like a configuration issue in libreville.
Open a document or spreadsheet, click on File>Printer Settings, a dialog box opens with title "Printer Setup". Your printer should be described in the fields: Name, Status, Type. Location and Comment may or may not have entries. You can refer to CUPS default printer for the necessary information that goes in those fields.

Added: I just reread your original post; I had missed the part about  *system-config-printer* and *system-config-printer*
What happens if you select the other printer as the default printer?
If it were me, I think I would delete both printers shown in *system-config-printer* followed by a reboot and reinstallation of the two printers.

---

### Post by alansecker on 2019-03-18
I followed your suggestion.
It made no difference.

---

