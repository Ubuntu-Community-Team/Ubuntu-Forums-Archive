---
title: "HP Deskjet F4280"
date: 2013-07-09
forum: General Help
---

### Post by va7ani on 2013-07-09
Running Ubuntu 12.04.
Done something to keep the printer from working properly.
Its not a hardware problem. I created another partition and installed  a fresh copy of ubuntu 12.04 and the printer auto-installed and works properly.
I deleted the printer from my working partition and rebooted ubuntu and it re-instals the printer but the symptoms remain.
Applications > System Tools > System Monitor > Printers
pop up box shows
active print jobs > currently 4 jobs listed, one status show "processing" the next 3 jobs show "pending"

I tried the scan operation e.g.
Simple Scan and it works ok.

I've gone to the web interface for CUPS and haven't spotted any obvious error messages.
Any suggestions ?

Walter
VA7ANI

---

### Post by va7ani on 2013-08-13
Any body come up with some ideas yet to solve my problem?

VA7ANI

---

### Post by kurt18947 on 2013-08-13
Have you tried creating a new temporary user and print from there?  It works properly from a new install so I'd suspect a 'crossways' file or setting.  If you can print from the problem install when logged in as a new user,  I'd suspect some .file problem in the the current user's home folder.  Beyond that, I don't really have any idea what files would be suspect.  Sorry I can't be of more help, good luck resolving your problem.

---

### Post by va7ani on 2013-08-14
Problem solved. I un-installed CUPS, rebooted Ubuntu, re-installed CUPS, rebooted Ubuntu and let it auto-detect my printer, then entered APPLICATIONS > SYSTEM TOOLS > SYSTEM SETTINGS > PRINTERS and made sure the printer was turned on.
I suspect a file pointer was pointed in the wrong place or crossed wired files.
Removing and re-installing CUPS cleared the problem.

Walter
VA7ANI

---

