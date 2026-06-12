---
title: "XSane"
date: 2013-01-23
forum: General Help
---

### Post by Kruxoli on 2013-01-23
Hi, I am having a small issue.  I have my computer connected to my Brother MFC-7860 DW and I can print with no issues.  To scan, I need to run XSane as a root user, and I can scan no problem.  My issue comes with the file.  I select the PDF extension and where to save the file.  OK.  No problem.  Only thing is, I can't open the PDFs that I scan.  I get the following error message:

There was an error opening this document.  You do not have permission to write to this file.

Is there any way to set XSane so that I am the owner of the scans?

Thanks, I really appreciate any help!

---

### Post by Kruxoli on 2013-01-23
> **Kruxoli said:**
> Hi, I am having a small issue.  I have my computer connected to my Brother MFC-7860 DW and I can print with no issues.  To scan, I need to run XSane as a root user, and I can scan no problem.  My issue comes with the file.  I select the PDF extension and where to save the file.  OK.  No problem.  Only thing is, I can't open the PDFs that I scan.  I get the following error message:

There was an error opening this document.  You do not have permission to write to this file.

Is there any way to set XSane so that I am the owner of the scans?

Thanks, I really appreciate any help!

I was actually able to figure this out on my own (SHOCKING!).

From XSane:

Preferences > Setup > Save

From here I was able to change the "User" and "Group" permissions allowing me to open the PDF files that I scanned.

THANKS!

---

