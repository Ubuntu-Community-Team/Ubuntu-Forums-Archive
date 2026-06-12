---
title: "Xsane not scanning properly with Epson Perfection 1240"
date: 2007-09-18
forum: General Help
---

### Post by modmidget on 2007-09-18
I am running Ubuntu Fiesty Fawn on a desktop computer and have attached an Epson Perfection 1240 Photo scanner.  Xsane recognizes the scanner OK but when I try to scan anything it only gets the left half of the page/document.  It looks like someone tore the page in half from top to bottom and the right side is gone.

Any ideas on how to correct this?  :confused:

Thanks much.

---

### Post by modmidget on 2007-09-19
^

---

### Post by modmidget on 2007-09-21
^

---

### Post by thrice_loved on 2007-12-13
Have a look in the settings of xsane.
One setting is the Top-left Bottom-right setting. When the top is lower than the bottom setting, or the right is further left than the 'left' setting it cannot scan.

They are found in "window" > "Advanced Options"

Set the first two to zero (left hand side) and the other two to whatever your maximum is (right hand side). This fixed the problem for me. Also if it doesn't stay that way you can save the scanner settings so that this change is permanent.

---

