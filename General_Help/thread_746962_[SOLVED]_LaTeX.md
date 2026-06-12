---
title: "[SOLVED] LaTeX"
date: 2008-04-06
forum: General Help
---

### Post by dstein on 2008-04-06
When I try to use \includegraphics{graphic.eps} in LaTeX, the DVI file only has a border of what should be the image. However, if I convert the EPS to PDF and use pdflatex, it works fine. Any ideas what would be preventing LaTeX from working with my EPS files? Thanks.

---

### Post by dstein on 2008-04-06
It seems that the graphic displays properly upon conversion to PS format. It seems DVI documents don't display images, but rather just their borders. Please let me know if this is the case. If not, there must be something wrong with my viewer or something I'm doing when running Latex or editing my file. Thanks.

---

### Post by dvase on 2008-04-08
What DVI viewer are you using?

---

### Post by dstein on 2008-04-08
Evince Document Viewer. Are there some DVI viewers that display images? On the wikipedia page for DVI, it says the following:
"Note that referenced images are not displayed, because they are not part of the DVI file. Images will be added in by a print driver, such as dvips."

---

### Post by dvase on 2008-04-08
> **dstein said:**
> Evince Document Viewer. Are there some DVI viewers that display images? On the wikipedia page for DVI, it says the following:
"Note that referenced images are not displayed, because they are not part of the DVI file. Images will be added in by a print driver, such as dvips."

My understanding of a DVI file is that it tells the DVI viewer where the original image is located in the system file directory.  It is up to the DVI viewer to decide if it should or can display the image.

I just opened a DVI file on my system with evince, and sure enough, I also see a black square frame around where the images should be.

I usually use KDVI for viewing DVI files, which displays images.

---

### Post by frisket on 2008-04-09
> **dvase said:**
> My understanding of a DVI file is that it tells the DVI viewer where the original image is located in the system file directory.  It is up to the DVI viewer to decide if it should or can display the image.

I just opened a DVI file on my system with evince, and sure enough, I also see a black square frame around where the images should be.

I usually use KDVI for viewing DVI files, which displays images.

DVI files do not *contain* the image, like PDF files do. but DVI *viewers* will display the image if told to do so (the default). If the image is not showing, you have either got the draft option applied for your graphicx package, or you're using AUCTeX Emacs, which nastily disables images.

I use xdvi and it always shows my EPS images just fine. Except with $%^&*( AUCTeX

///Peter

---

