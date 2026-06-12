---
title: "Viewing PDFs in a way that treats hyperlinks/history properly? Evince seems bugged."
date: 2015-03-30
forum: General Help
---

### Post by Zorgoth on 2015-03-30
I'm currently using Ubuntu 14.04 and evince.

I'm working on a huge paper in LaTeX, and I view it on the computer by using pdflatex to make it a pdf. I recently added hyperlinks to the equation number citations in my document (using the LaTeX package hyperref), and I can click on the hyperlinks in evince to get where I need to go, but the back button will not take me back to the original link, but rather only to the page at which I opened the document. Does anyone know how to either fix this behavior in evince or of another PDF viewer that meets the following criteria:

1) Reads PDFs "dynamically" - that is to say, when the PDF changes on the drive, the viewer will update it (evince meets this criterion)
2) Fast with a minimal resource footprint and interface (evince meets this criterion)
3) Handles hyperlinks and history correctly (evince appears not to meet this criterion)

---

### Post by Zorgoth on 2015-03-30
qpdfview seems to meet my needs, after enabling Settings>Behavior>Auto-refresh and disabling Settings>Graphics>Decorate Links.

---

