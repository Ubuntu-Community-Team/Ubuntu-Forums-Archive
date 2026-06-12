---
title: "Printing to .pdf"
date: 2005-06-19
forum: General Help
---

### Post by toyfactory on 2005-06-19
Hi,

I'm having problems printing to .pdf files.  OpenOffice does the job OK,
but I want to print to .pdf from Firefox too.

I've tried printing to .ps file and the resulting file looks fine in the 
GhostScript viewer but I can't get it to convert to .pdf; both Acrobat
for Windows and ps2pdf produce unreadable files (no or garbage text).

I've also tried using CUPS-PDF but that produces exactly the same 
unreadable output as ps2pdf.

This functionality is one thing on my (slowly diminishing) list of things 
I still need Windows for!  Anyone have any suggestions on getting it
working in Ubuntu?

Cheers,

Nick

---

### Post by angrykeyboarder on 2005-06-20
[QUOTE=toyfactory]Hi,

I'm having problems printing to .pdf files.  OpenOffice does the job OK,
but I want to print to .pdf from Firefox too.

I've tried printing to .ps file and the resulting file looks fine in the 
GhostScript viewer but I can't get it to convert to .pdf; both Acrobat
for Windows and ps2pdf produce unreadable files (no or garbage text).

I've also tried using CUPS-PDF but that produces exactly the same 
unreadable output as ps2pdf.

This functionality is one thing on my (slowly diminishing) list of things 
I still need Windows for!  Anyone have any suggestions on getting it
working in Ubuntu?

Cheers,

Nick[/QUOTE]

I've had exactly the same problems and can't find a solution either.

I'm surprised someone hasn't written an open-source "print to pdf" driver like they have for [Windows]("http://sourceforge.net/projects/pdfcreator/").

---

### Post by toyfactory on 2005-06-20
Some people report success using the CUPS-PDF driver.  I can use it to print to .pdf in other applications, but it doesn't solve my FireFox printing problem.  I'm beginning to suspect it's some strange config or font problem but I don't know where to begin solving it!

Nick

---

### Post by angrykeyboarder on 2005-06-20
[QUOTE=toyfactory]Some people report success using the CUPS-PDF driver. I can use it to print to .pdf in other applications, but it doesn't solve my FireFox printing problem. I'm beginning to suspect it's some strange config or font problem but I don't know where to begin solving it!

Nick[/QUOTE]

Well I happend upon [http://xprint.mozdev.org/]("http://xprint.mozdev.org/") just now and it seems that some of the binaries are in .deb form in the Hoary Universe archive (why some and not all, I don't know).

---

