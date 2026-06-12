---
title: "font issue"
date: 2014-03-28
forum: General Help
---

### Post by Rob_Butland on 2014-03-28
I've been using WINE to run photoshop 7, and everything works fine except the text tool. It says a default font cannot be located. 

Can anybody direct me to a walk through that will help me get this sorted? If I can't do it i'm going to have to go back to windows! Save me!!!!!

Many thanks

Rob

---

### Post by alex2e1gzy on 2014-03-28
Have you installed the restricted-extras package (check box during install)? It contains some of the Windows fonts you might need. Otherwise can you see what font it is trying to load and post back?

Maybe this would help: [http://ubuntuforums.org/showthread.php?t=2184107](http://ubuntuforums.org/showthread.php?t=2184107)

---

### Post by grahammechanical on 2014-03-28
An installation of Wine usually installs the Microsoft True Type core fonts installer which in turn will install Microsoft core fonts which Windows programs expect to find. We do need to accept the Microsoft End User licence. It may be possible to install Wine without accepting the Microsoft End User license. It which case we get this problem.

As a tip, when installing wine or the Restricted Extras package or the Microsoft core fonts installer, we should minimise the Software Centre application window as the End User License appears behind the software centre window and we will not know it is there waiting for input.

Look in the software centre for ttf-mscorefonts-installer

Regards.

---

