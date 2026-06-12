---
title: "Mangled PDF Printer Output"
date: 2008-04-09
forum: General Help
---

### Post by rwk32882 on 2008-04-09
I run the standard desktop edition of Ubuntu 7.10.  I am having some issues printing PDF files to paper (I'm NOT attempting to create PDF files.).  My printer is a network attached HP Laserjet 4250 and I am using the Postscript driver that comes with Ubuntu.

Initially, I thought the problems I've been experiencing were being caused be a corrupt PDF file or two.  Recently however, I've been running into this problem more and more often so I'm beginning to suspect that there is an issue with the viewer (using evince), print driver, or possibly something in between (pdf->ps conversion process?).  The end result is a partially or fully printed document plus a bunch of random lines on top of the text with many of them originating in the upper-left corner of each page.

One workaround that I tried was regenerating the PDF by using evince to print it to a secondary PDF file.  The resulting PDF file contains the same artifacts that I see on the actual printed document.

A second workaround that I tried actually solved the problem.  I simply executed a ```
lp myfile.pdf
``` from the command line.  The print job looked correct in this case.

What are the differences between a print job that starts from evince and one that is initiated from the lp command?

If anyone is interested in seeing the output that I'm observing (as well as the original PDF file that I am trying to print) you can find those [here]("http://www.mit.edu/~kingryan/pdf_debug/").

TIA, let me know if I can provide any additional details that would be useful.

---

