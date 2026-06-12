---
title: "command line printing problem"
date: 2007-04-16
forum: General Help
---

### Post by akirashinigami on 2007-04-16
When I try to print a file that doesn't fit on a single page using lpr in bash, there are 3-4 lines that don't get printed in between pages.  This doesn't happen if I print from gedit or OpenOffice, and stuff like that.  Does anyone know how I could fix that?  I'm running Ubuntu 6.10, and my printer is an HP Deskjet 3740, if that helps.

---

### Post by fanatik on 2007-04-17
is it because /etc/papersize is set incorrectly? Are you printing to letter when it's set to a4 or vice versa?

---

### Post by akirashinigami on 2007-04-17
Well, I'm printing to letter size paper, and /etc/papersize said a4.  So I changed /etc/papersize to letter, but it didn't do anything.  I tried a bunch of different values in /etc/papersize to see if I could make it do *something,* but none of it changed anything.

---

### Post by akirashinigami on 2007-04-17
Ok, never mind, I fixed it.  I went into System > Administration > Printing, went to properties for my printer, and set the paper size there.  Then it worked.

---

