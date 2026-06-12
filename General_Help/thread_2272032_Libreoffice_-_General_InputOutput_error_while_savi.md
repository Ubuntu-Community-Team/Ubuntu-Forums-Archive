---
title: "Libreoffice - General Input/Output error while saving file in Writer"
date: 2015-04-03
forum: General Help
---

### Post by fcigoi on 2015-04-03
It has occurred quite a few times that Libreoffice Writer has terminated with a "General Input/Output Error" message that has greyed out all icons and menus while trying to save a file to the PC internal drive.

This way I have lost several pages of an important piece of work that I will have to rewrite.

Is the program so unreliable in general ? Is it a known bug ? Any ways around it ?

Alternatively, is there a way to install Microsoft Office under Linux ? I am using the 64 bit version of Ubuntu 14.10, and definitely need a word processor that doesn't force me to type everything twice.

---

### Post by TheFu on 2015-04-03
a) if you need stability, run 14.04.  14.10 only has 9 months of support. The same for the upcoming 15.04. You and I need to stay on LTS releases.
b) if you can't lose anything have backups made constantly. There are tools for that like back-in-time.
c) No - libreoffice is NOT unstable. Something about your setup is wrong, bad, failing.  Either software or hardware. **Check the log files.**
d) Some versions of MS-Office can be run under WINE. I think I got Office 2003 working a few years ago. appdb.winehq.org will have steps.

So - check the log files for any errors or warnings and resolve those.  I suspect there is an issue with a HDD or a cable, but the logs should be clear about that.  I'd also see what else is running that might be causing the system to run out of RAM. Some programs behave badly when there isn't any more RAM.

While highly unlikely, reinstalling libre office might help.

Good luck.

---

