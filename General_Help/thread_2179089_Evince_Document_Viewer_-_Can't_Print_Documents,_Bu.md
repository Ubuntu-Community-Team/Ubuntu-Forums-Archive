---
title: "Evince Document Viewer - Can't Print Documents, Button is Grey."
date: 2013-10-06
forum: General Help
---

### Post by jervin2 on 2013-10-06
I print fine in LibreOffice, from Web Browsers etc.  But from the Document Viewer that comes with Ubuntu, the Print menu button is Grey'd out.  
[LIST]
[*]I have googled and have not found anything particularly helpful.  
[*]I can view PDF files in Document Viewer, with no problem, just no print.  
[*]I can view in Adobe Reader and Print.  The document in question is not print protected and I have the option to bypass restrictions checked anyway.  
[*]I have removed and re-installed Document Viewer w/o success.
[*]Document Viewer 3.6.1
[*]Ubuntu 13.04 at current maintenance as of today.
[/LIST]


Any ideas..

---

### Post by DuckHook on 2013-10-06
Are the PDFs non-printable? Some publishers turn on the security feature in their PDFs that incapacitates printing and copying.

---

### Post by jervin2 on 2013-10-11
The PDF files are not non-printable.

---

### Post by slickymaster on 2013-10-11
What happens when you hit Ctrl+P simultaneously?

---

### Post by vasa1 on 2013-10-11
> **jervin2 said:**
> I print fine in LibreOffice, from Web Browsers etc.  But from the Document Viewer that comes with Ubuntu, the Print menu button is Grey'd out.  
[LIST]
[*]I have googled and have not found anything particularly helpful.  
[*]I can view PDF files in Document Viewer, with no problem, just no print.  
[*]I can view in Adobe Reader and Print.  **The document in question is not print protected** and I have the option to bypass restrictions checked anyway.  
[*]I have removed and re-installed Document Viewer w/o success.
[*]Document Viewer 3.6.1
[*]Ubuntu 13.04 at current maintenance as of today.
[/LIST]


Any ideas..
So you have a problem with **one** document or with documents from **one source**? Is it correct that you don't have problems printing pdf files in general with Evince?

---

### Post by jervin2 on 2013-10-13
Cntl-P also does not work at all.  

BTW, in case I didn't mention it earlier, I do have several printers on my system that print from other apps, including Adobe Reader for the same PDF's.

---

### Post by slickymaster on 2013-10-14
As you don't seem to have a printer communication problem, it could be that your cups filter that converts PDF print jobs into Postscript for printing is not installed, misconfigured, or broken - possible.

---

### Post by jervin2 on 2013-10-14
Anything is possible, it's the ppd is supposed to be the correct one that comes with hplip for the hp deskjet 895Cxi printer.  Not sure about conversion to Postscript.

---

