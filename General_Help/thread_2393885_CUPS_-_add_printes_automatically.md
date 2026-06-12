---
title: "CUPS - add printes automatically"
date: 2018-06-09
forum: General Help
---

### Post by Argonisius on 2018-06-09
Hi,

I would like to setup CUPS so it automatically ads discovered printers (both local and network). Is it possible? My idea is that I plug the printer to my USB and it gets added to the system automatically so I can print straight away (plug'n'play).

Thank for your ideas.

---

### Post by ajgreeny on 2018-06-09
I think some printers, and it must depend on the maker and driver situation for the particular model, are already discovered and enabled without the user doing anything.

That was certainly the case with my Xubuntu 18.04 which found my HP Envy 4520 via wifi with no action from me at all.
I have also installed it using the hplip-gui toolbox as it makes managing the printer a lot easier, so now I have two instances of the same printer,  one from cups, the second from hplip.

---

### Post by bodhin2 on 2018-06-09
my wireless hp was auto detected.  no setup required.

---

### Post by oldfred on 2018-06-09
Something new in 18.04
       [https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes) 
    Driverless printing support is now available. 

PostScript Printer Description (PPD) files are created by vendors to describe the entire set of features and capabilities available for their PostScript printers.
Since used by Mac for years, most printers now support PPD files.

My HP Envy 4500 was automatically found.

---

