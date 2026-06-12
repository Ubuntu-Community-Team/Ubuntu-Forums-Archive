---
title: "Completely stumped on a problem with LibreOffice..."
date: 2014-04-25
forum: General Help
---

### Post by vperaino on 2014-04-25
Alright, so. 

All of the computers in our office are running 12.04. 

We have a Konica Minolta Bizhub 363 MFP set up as the main printer for the office. It's installed using the driver in the default printer database in the printer settings on all machines. 

All of the computers can print to the Konica. Documents, PDFs, web pages, etc. all print just fine...except for one instance. 

Whenever one particular machine prints something out of any of the LibreOffice applications, the printer freezes, and it needs to be power cycled. The cruel irony is that this person's computer is the only one that typically does stuff in LibreOffice. 

Every other computer in the office can print from LibreOffice just fine, except this one. The computer in question can print anything with no issues, except in LibreOffice. 

The computer is hooked up to the same network switch, etc. that a fully-functioning computer is hooked up to, so there's no hardware issue. 

I have compared the printer settings, both in the printer administration and inside LibreOffice, to a working machine. They are, as far as I can tell, identical. 

Any ideas?

EDIT: Forgot to mention, the computer in question can print out of LibreOffice to a Brother HL-2270DW.

---

### Post by amanchesterman on 2014-04-26
It's not clear from your post whether the machines in your office are running Linux or another OS. However I am assuming they are since you have asked in a Ubuntu forum.

In that case the most relevant information I have found is here: [http://straightbanana.wordpress.com/2012/10/16/konica-minolta-bizhub-c220-network-printer-on-linux-mint/](http://straightbanana.wordpress.com/2012/10/16/konica-minolta-bizhub-c220-network-printer-on-linux-mint/) . It's not quite the same model of printer and not quite the same version of Linux that you have, but the diagnosis and solution may be relevant for you.

Failing that, search online for 'konica bizhub print libreoffice' (or variations thereof) and you will find quite a few posts and discussions.

---

### Post by Peter Maunder on 2014-04-26
Assuming that it is just one of the 12.04 systems, just one of the printers (Konica) on LibreOffice only and you have to re-cycle the printer, you don't have a different paper size default in LibreOffice for this printer do you? For example, if the paper size is set to Letter and the Printer is A4, you would have a similar problem. the inverse is also true, A4 for Letter.

---

### Post by vperaino on 2014-04-28
Sure enough, switching the printer language from "PDF" to "postscript, driver level" enabled me to print from the machine in question. 

Still don't know why it's only that machine, but hey, I've got my solution! :)

---

