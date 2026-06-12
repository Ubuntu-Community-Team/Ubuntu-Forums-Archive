---
title: "lpr just partly work...."
date: 2006-11-20
forum: General Help
---

### Post by ked on 2006-11-20
Hi all,

I'm trying to get lpr to direct my documents with the -P argument, but it just returns the "lpr: error - unable to print file: client-error-not-found" I've seen a lot of cups related answers in the forums, but nothing that has solved my problem. The strange thing is that lpr works just fine if I don't use any arguments - like:

>lpr doc.pdf

and I can choose the default printer via the configuration tool from the menu:

System > Administration > Printing

and printing is no problem from the command line. But if I try to direct the document like:

>lpr -P some.network.printer doc.pdf

it wont work. Another thing is that I can't get the queue set in the printer properties configuration.

Anyone any idea why lpr just works partly?

(I'm running Breezy and our printers are UNIX network (LPD) postscript printers)

Regards,
Ked

---

### Post by bettlebrox on 2006-11-20
Do you have the cupsys-bsd package installed? That should contain a version of lpr that works with CUPS.

---

### Post by ked on 2006-11-22
Yes I have have the cupsys-bsd package installed, and I find this bug very, very strange. All printing works from all programs (emacs, ooffice2, gv, acroread etc.) but just partly from the terminal prompt. From here I can't use any argument. I really like to use the -P option as we have several printers here for different use.

---

