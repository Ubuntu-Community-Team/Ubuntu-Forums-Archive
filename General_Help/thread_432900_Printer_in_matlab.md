---
title: "Printer in matlab"
date: 2007-05-04
forum: General Help
---

### Post by stee on 2007-05-04
I have a problem getting printes to work in Matlab (R2007a).
-I'm using Kubuntu Feisty. 
-The printer is a (samba) network printer which I've set up with KDE Print, using cups. 
-It works perfectly from every other application, but in matlab I get a message that no printers are installed.

I found this page: [http://www.mathworks.com/support/solutions/data/1-1A8XJ.html?solution=1-1A8XJ](http://www.mathworks.com/support/solutions/data/1-1A8XJ.html?solution=1-1A8XJ)
and tried to edit printopt.m, adding the following line (Planck is the name I gave the printer in KDE print):
pcmd = 'lpr -s -r -PPlanck'

Still the same error message.

I hope there's someone who can help me!

---

### Post by stee on 2007-05-05
Noone?

---

