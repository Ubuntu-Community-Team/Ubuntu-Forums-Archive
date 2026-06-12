---
title: "cups-pdf custom page sizes"
date: 2008-05-22
forum: General Help
---

### Post by Go_Bucks on 2008-05-22
Howdy,

Cups-pdf has an option for "custom" under page sizes, but then there is no option to set your custom page size. How do I do this?

I am asking because I have the following issue:

I use a GIS program called gvSIG. It has an export to PDF function, but when viewed in Adobe Reader on all operating systems the PDF it produces is VERY GREEN. It looks fine in almost anything else. So, what I have been doing, is pull that PDF into GIMP and re-print the PDF through the PDF printer and that works fine. 

Now, however, I have a graphic that is poster-sized (24 inches x 48 inches). I can set that as the print size in GIMP, but GIMP never communicates the correct page size to the PDF printer, so I have to tell the PDF printer as well what size to use. Therein lies my problem... no option in CUPS to set the page size in Custom.

---

### Post by Go_Bucks on 2008-05-22
BUMP... someone must know the answer...

---

### Post by noynac on 2008-05-23
> **Go_Bucks said:**
> Howdy, Cups-pdf has an option for "custom" under page sizes, but then there is no option to set your custom page size. How do I do this?...

I believe the cups-pdf custom-page-size setting utilizes the paper size of the source document. For example, I created a document with gedit and set the paper size at 5 by 2 inches using page setup. I then printed this using cups-pdf with paper size set at custom. Finally, I opened the resulting PDF document in Evince and checked the paper size--it was 5 by 2 inches. I did this a second time with a gedit paper size set at 5 by 3 inches, and the PDF was 5 by 3 inches.

---

### Post by Go_Bucks on 2008-05-23
That is what I figured the behavior to be, but it wasn't accepting the custom page size from GIMP. I just tried it from Document Viewer and it worked fine.

---

