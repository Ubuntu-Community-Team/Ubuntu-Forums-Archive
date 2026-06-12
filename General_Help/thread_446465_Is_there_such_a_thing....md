---
title: "Is there such a thing..."
date: 2007-05-17
forum: General Help
---

### Post by Dimension7 on 2007-05-17
Is there such a thing for Linux/Ubuntu (a program, add-on, whatever you call it) that instead of printing it will be saved as a file?  More of like a Paperport or Acrobat for Windows?

For example I'm browsing the web, I saw something I want to print so I'll click the print button, but when the print dialog shows up, I'll just select the printer name and it will be saved as a file rather than print directly to the printer.

I hope I explained clearly what I really wanted to do.  My English is not good.

---

### Post by jtraub on 2007-05-17
By default Ubuntu has Postscript printer. It prints into ps files, that can be viewed with evince.

---

### Post by Dimension7 on 2007-05-17
Thank you so much.  That is exactly what I'm looking for.  
However, where does this postscript or ps file located by default as I cannot find it in my /home/<user>/ directory?  I tried it several times but it doesn't show on my /home.

---

### Post by dustigroove on 2007-05-17
[FONT=Arial][SIZE=2]The package you are looking for is in the repositories as "cups-pdf".


From the description:[/SIZE][/FONT][INDENT][FONT=Arial][SIZE=2][SIZE=1]*"PDF printer for CUPS*[/SIZE][/SIZE][/FONT]
[FONT=Arial][SIZE=2][SIZE=1]*CUPS-PDF provides a PDF Writer backend to CUPS. This can be used as a*[/SIZE][/SIZE][/FONT]
[FONT=Arial][SIZE=2][SIZE=1]*virtual printer in a paperless network or to perform testing on CUPS.*[/SIZE][/SIZE][/FONT]

[FONT=Arial][SIZE=2][SIZE=1]*Documents are written to a configurable directory (by default to ~/PDF)*[/SIZE][/SIZE][/FONT]
[FONT=Arial][SIZE=2][SIZE=1]*or can be further manipulated by a post-processing command.*[/SIZE][/SIZE][/FONT]

[FONT=Arial][SIZE=2][SIZE=1][I]Homepage:  http://cip.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/"
[/I][/SIZE][/SIZE][/FONT][/INDENT][FONT=Arial]Cheers,[/FONT]

---

