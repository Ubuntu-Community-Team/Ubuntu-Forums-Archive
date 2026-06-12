---
title: "cups/pdf pdf-printer creating corrupted pdf documents[Solved]"
date: 2007-10-22
forum: General Help
---

### Post by zerodamage on 2007-10-22
I've noticed that when I create a PDF document using the built in pdf-printer in Gutsy, I can open in Ubuntu just fine when only wanting to view.  If I want to edit the file with PDF editor  or view in Windows using Adobe Reader, it tells me that the file is corrupted or encoded wrong.  This defeats the purpose of having this feature if the only thing that I can do is view the documents only in Ubuntu and the "Portable" part of the PDF file isn't really portable.  Is there a way to fix this?   I've tried to use the deafult postscript option and the cups/pdf option when printing and they both cause these problems.  (I am using the print to file option, could this be the problem?)

---

### Post by zerodamage on 2007-10-22
I figured it out.  It looks like "print to file" is the problem.  If I just use the CUPS/PDF option without the print to file option checked it works fine.  How annoying.

---

