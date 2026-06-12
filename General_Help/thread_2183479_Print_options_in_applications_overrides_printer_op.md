---
title: "Print options in applications overrides printer options"
date: 2013-10-25
forum: General Help
---

### Post by grizzly_ripper on 2013-10-25
I have a problem, that I first experienced at Epson XP-33 and Epson XP-207, but it proved to be common for other printers as well.


I print different pages in different sizes (small photos, large photos, color print, b/w text). In Windows I did it by creating a copies of my printer in the system, setting separate print options for each printer for each print format. It worked fine - you choose a printer, it prints what and how you want it.


But when I try that in Ubuntu 12.04 it turns out that the applications do not care about the the options of the printers. They keep their own settings. Moreover they do not just keep their own options, but somehow it 'spreads' to other printers. E.g. I send a colored A4 to print in Evince but it prints it in b/w, as b/w was the last print option. If you choose the other printer the options from last print task are already there, though I expect them to print with the option predefined on a printer.


What would be the cause of it and the way out?

---

### Post by coldraven on 2013-10-25
I'm guessing that all your printer versions are using the CUPS print server. I'm also guessing that CUPS looks at the actual hardware and sees the same printer.    
There should be a way to do what you want, hopefully someone knows how.
[http://en.wikipedia.org/wiki/CUPS](http://en.wikipedia.org/wiki/CUPS)

---

