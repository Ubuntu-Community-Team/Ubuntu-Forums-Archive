---
title: "How to create a PDF A5 booklet?"
date: 2007-01-24
forum: General Help
---

### Post by MadeR on 2007-01-24
Here is my question:
suppose i created a 8-page A5 document.
I desire to print it on a A4 sheet having 2 pages on each sheet.

But I want the pages to be in booklet order:
1&8, 2&7, 3&6, 4&5. If I printed each sheet on both sides and then folded the sheet along the central line, I would create a small book.

Is there a tool to accomplish this? the best way would be a cups add-on...

---

### Post by pestilence4hr on 2007-05-03
You can accomplish this using the command-line utility "psbook".  First, use pdf2ps to convert to a postscript document.   Then use psbook to reorder the page for booklet-style printing.  Then you can either a) convert back to pdf using ps2pdf14 and print using acrobat, doing duplex (flip on short edge) and 2 pages per sheet, or b) using mpage and a duplex print mode in cups.

---

### Post by otto67 on 2007-12-20
I made a small script in my home folder and a shortcut of this (booklet) on my desktop.
In any program, when printing, choose option "Print to file.."
Choose the location "Desktop" and a filename with extension "ps" , f.ex. "out.ps"
Then run the script- (or more simple - click the script shortcut on your Desktop)
in couple of seconds you will have a file named "dokument.pdf" on your Desktop.
This is the pdf with booklet layout. Print it out with duplex - short edge.
Thats it!

---

