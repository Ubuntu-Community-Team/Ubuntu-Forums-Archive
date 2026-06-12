---
title: "Editor problems with gedit and nedit"
date: 2007-06-10
forum: General Help
---

### Post by penman242 on 2007-06-10
I'm using 704 on x86 (pentium 4).  I have installed a barebones system using the mini.iso and then installed xorg, fluxbox, etc.  It is a very fast and responsive.  However, I have to use two editors, nedit and gedit, because of various problems.

Nedit prints using every square cm of the page, which is good for conserving trees but makes it difficult to use a hole punch.  I can find no settings for margins in nedit.

Gedit, on the other hand, prints very nicely with margins.  But if I try to save a document in gedit, the save dialog box comes up but the right end of it is constantly jumping to the right and the left.  The save and cancel buttons are jumping, too.  I tried to hit the buttons but it was like trying to topple the bottle stacks at the fair.  I never could hit the save one.

sudo aptitude search gedit         shows that both gedit and gedit-common are installed.  I also installed gedit-plugins.

Does anyone know how to fix the jumping gedit save dialog box problem?  I know I have seen a post on this but now I can't assemble the correct search terms to find it.

---

### Post by kerry_s on 2007-06-10
try geany and gtklp for the printer in geany.

sudo apt-get install geany gtklp

in the geany settings for printer put gtklp and set up gtklp with the settings you want.

---

### Post by penman242 on 2007-06-10
Perfect!  I like it.  Set the margins to 54 (x4) and selected Wrap text, both within the Text tab of gtklp.  Clicking Save As, Save, Ok made the new settings permanent.  One thing I did notice was I had to remove a space from the text file name.  I guess its probably best not to have spaces in file names anyway.

Thanks a bunch for your reply!

---

