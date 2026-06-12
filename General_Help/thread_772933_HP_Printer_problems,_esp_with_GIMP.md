---
title: "HP Printer problems, esp with GIMP"
date: 2008-04-28
forum: General Help
---

### Post by lauriejb on 2008-04-28
Having had an Epson 890 run perfectly in Feisty on a Dell desktop I have swapped it for an HP 7360.  The preferred option in CUPS is HP 7300 series.  On B&W text there are no problems with Open Office, etc.  It works a treat.  In the GIMP there is no specific 7360 option, but I assume that a 7300 generic setting will be OK.  Three problems here however.

Colour is far too red - and the colour bars in the advanced print setting are greyed out.  This could be the paper because I cannot load the photo paper that I have, but I suspect not, somehow.

It insists on only printing only half of an A4 photo page, and then throws the paper but still insists that it is printing (in the LCD display on the printer).

It refuses to pick up photo paper from the photo tray whatever setting I try in the GIMP or the default system dialog.

Any ideas anyone?

---

### Post by danwood76 on 2008-04-28
Does the ubuntu test page print ok?
It prints different shades and colours, this will narrow down whether its a general printer driver issue or with the GIMP.

You can print the test page by going System -> Administration -> Printing

---

### Post by lauriejb on 2008-05-03
Thanks for that tip.  It prints a test page OK (well, apart from chopping the top off slightly, but I'll wear that) so it must be the Gimp.  So, next move?  

I should have said that I have since tried printing by dropping an image onto a CF card and plugging that directly into the printer, and that all worked, so the printer itself seems to be OK.

---

### Post by danwood76 on 2008-05-04
You could try installing the gutenprint plugin for gimp.
The exact package name is 'gimp-gutenprint' search synaptic for it.

Then when you want to print choose 'print with gutenprint' and see if it gives better results then just with straight cups.

---

