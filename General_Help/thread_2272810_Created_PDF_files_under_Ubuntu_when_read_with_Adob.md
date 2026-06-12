---
title: "Created PDF files under Ubuntu when read with Adobe are blank"
date: 2015-04-08
forum: General Help
---

### Post by janeku2 on 2015-04-08
Hello.
I have a very strange issue.
All documents created with Open Office (OS:Ubuntu 14.04.2 32-bit) and after that Exported to PDF or Printed to PDF , when opened with Adobe reader under Windows are blank ? Fox Reader read created file normal.
Same file opened under Ubuntu with Adobe or other PDF reader is OK.
What is the problem ??? Somebody experienced the same ?
Regards,

---

### Post by Impavidus on 2015-04-08
I guess it has to do with missing fonts. OOffice creates PDFs with the fonts not embedded. The same font has not been installed on Windows and the reader can't choose a reasonable fallback, so no font is shown at all. The solution is either to ensure all fonts are embedded in the PDF or to make sure OOffice uses fonts installed on Windows. I never tried either of those solutions as I never had that problem, but this will give you a lead in your search for a solution.

---

### Post by grahammechanical on 2015-04-08
We need to export the document in the PDF/A-1a format. File>Export As>PDF Options and tick the box labelled Archive PDF/A-1a (ISO 19005-1). Libreoffice Help says:

   > [h=3]PDF/A-1a[/h] Converts to the PDF/A-1a format. This is defined as an electronic document file format for long term preservation. All fonts that were used in the source document will be embedded into the generated PDF file. PDF tags will be written.



Regards.

---

### Post by janeku2 on 2015-04-09
> **grahammechanical said:**
> We need to export the document in the PDF/A-1a format. File>Export As>PDF Options and tick the box labelled Archive PDF/A-1a (ISO 19005-1). Libreoffice Help says:

   

Regards.

Looks like this helped.
I do not know why but after choosing PDF/A-1a, created document is readable under Windows Adobe Reader.
As I can remember, this option wasn't selected from begining, but now doesn't matter.
Also I installed cups-pdf in order to secure potentialy bad created PDF from OOfice.
So, case closed :)
Thank you very much.
Stay well.

---

