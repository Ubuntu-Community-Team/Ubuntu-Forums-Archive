---
title: "Help please - printing PDF file to HP Deskjet 9800"
date: 2007-10-15
forum: General Help
---

### Post by wb0gaz on 2007-10-15
Ubuntu 7.04, with HP Deskjet 9800 connected via USB port. Need to print a PDF file which is scaled up from it's source size (8-1/2x11) to the paper size (11x17).

In other uses, printing is fine, so I believe the machine, Linux and the printer are getting along OK.

My application cannot directly generate Ledger size PDF file, but can generate letter (8-1/2x11) formatted output. My problem is how to scale the printed image so that I can scale to fit the larger paper.

I've set the printer's page size option to "Ledger". Printer "Make and Model" i shown as HP Deskjet 9800 Footmatic/hpijs.

Here's the symptoms I'm getting:

xpdf - has no mechanism I can see to scale the output, so it generates 8-1/2x11 in a corner of the paper.

Acrobat (/usr/bin/acroread - installed 8.1.1) - opens the file fine, lets me scale (fit to page, etc.), then crashes the printer (ejects a blank page, then red blinking light, must power-cycle.) lpstat shows a print job leftover that I must manually remove with "cancel" command, and then I must power cycle printer.

Ghostview (gv) - opens the file fine, then crashes the printer (same as Acrobat.)

Are there other ways to approach this?

Thanks,

Dave
[email]wb0gaz@hotmail.com[/email]

---

