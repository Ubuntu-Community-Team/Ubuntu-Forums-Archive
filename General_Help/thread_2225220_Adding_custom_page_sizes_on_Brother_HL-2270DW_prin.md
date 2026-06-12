---
title: "Adding custom page sizes on Brother HL-2270DW printer"
date: 2014-05-20
forum: General Help
---

### Post by dwlamb on 2014-05-20
I am trying to add a custom page size on a Brother HL-2270DW printer. Adding the page size by simply editing a PPD file is not sufficient. From a posting made to the cups.org mailing list I have learnt this and probably all Brother printers utilise a proprietary filter to translate the information into strings the printer uses. That file, a CUPS wrapper, I have downloaded the source code from the Brother support site. It is a simple bash script file but I do not know if editing this is sufficient to add the custom size I want. Does anyone have experience with this?


Researching solutions, I have seen a possible fix might exist using an HL-2170W driver and the HP Linux Imaging and Printing package. Can this be tried with the Brother LPR driver and CUPS wrapper printer driver already installed or do they need to be removed first? How does one remove those two driver packages? They were installed using a script downloaded from the Brother support site.

---

### Post by dwlamb on 2014-05-22
nudge

---

