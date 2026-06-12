---
title: "Printer does not work in OpenOffice only"
date: 2008-04-06
forum: General Help
---

### Post by cflusflwfl on 2008-04-06
I am currently using Ubuntu 7.10.  I have my HP Deskjet 932c working with everything except OpenOffice.  My printer shows up as an option in OpenOffice, but when I click to print, the printer starts and sends the paper through the printer.  It always comes out blank.  It seems that OpenOffice is communicating with my printer, but everything comes out blank.  This also happens if I save the OpenOffice file as a PDF and try to print the PDF file.

Thanks,
Steve

---

### Post by kyphi on 2008-04-07
I don't quite understand by what you mean when you say that your printer shows up in Open Office, mine doesn't.

Check that you have set your printer up correctly by going to System -> Administration -> Printing.  Right click on the printer icon and open Preferences from the drop down menu.  Go to Driver and you should see hpijs (recommended)-HPLIP 0.9.7 (suggested).

In OOo go to Tools -> Options -> OOo Writer -> Print and ensure that there is a tick next to 'Print automatically inserted blank pages'.

With that configuration both my 930C and 950C work perfectly.

---

