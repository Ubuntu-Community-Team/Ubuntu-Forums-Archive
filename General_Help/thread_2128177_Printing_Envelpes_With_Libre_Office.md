---
title: "Printing Envelpes With Libre Office"
date: 2013-03-22
forum: General Help
---

### Post by daniell59 on 2013-03-22
I tried to print an evelope in Libre Office. The sender address is too far to the right. It is listed as .39 inches. It is more like an inch away. Any assistance will be appreciated.

Ubuntu 12.04 64

---

### Post by kurt18947 on 2013-03-22
I have the same issue to a greater extent.  Unedited, my return address is about 1.5" from the left edge of the envelope.  It varies by printer, though so presumably it's a problem with the printer driver.  The print preview in Libre Office looks correct, the output is not.  One peculiarity I've noticed is the wrong envelope is selected. I do new document ->format ->page then select #10 Envelope.  Reset the margins to .5 all around then fill in the addresses.  Click 'print' -> <the 'problem' printer> -> properties, paper size shows up as 'DL', the paper size **above** the requested #10 envelope.  If I select #10 envelope there, it helps.  Just for grins I modified the .ppd file to make 'DL' the same as '#10'.  It didn't seem to help.  I finally settled on setting the left margin to .12", make sure #10 envelope is selected in properties and call it good.  Again, it is just this one printer, two others work as expected.  They're all 3 Brother printers so manufacturer doesn't seem to enter into the problem.  It just appears this one printer, 1st. generation large format printer is a problem, two others behave as expected.

---

### Post by daniell59 on 2013-03-22
I think that I have figured it out. I did the following. Insert-envelope-Printer, then envelope orientation. I tried different ones until it worked. For me the one in the middle worked.

---

### Post by kurt18947 on 2013-03-22
I'll have to try that, thanks!

---

