---
title: "Can't open .pptx files with LibreOffice ..."
date: 2021-03-13
forum: General Help
---

### Post by dbee on 2021-03-13
Get this error when i try to open .pptx files with LibreOffice...
> 
The file 'DM.pptx' is corrupt and therefore cannot be opened. LibreOffice can try to repair the file.

The corruption could be the result of document manipulation or of structural document damage due to data transmission.

We recommend that you do not trust the content of the repaired document.
Execution of macros is disabled for this document.

Should LibreOffice repair the file?


Need to open these docs for a class assignment. Doesn't seem to be a permission or data transmission issue.

Can't find a solution on Google...

---

### Post by CelticWarrior on 2021-03-13
> **dbee said:**
> Doesn't seem to be a permission or data transmission issue.
Indeed, it doesn't.
The error message explicitly says corruption.

Try WPS Office for better compatibility.

---

### Post by Holger_Gehrke on 2021-03-13
The *.???x Microsoft Office files are just zip-containers full of XML for textual content, structure and format and various other files for none-textual content similar to the ODF-formats used by Libre/OpenOffice. The difference between the formats is in the schemas used for the XML. This allow you to check the integrity of such a file with 'unzip -t /path/to/the/file'. If the file is a valid zip-archive the 'corruption' LibreOffice detects is actually a problem in it's import filter and you'll have to try some other program. If the file fails this test, then it is indeed broken and you should ask the person who gave it to you for a good copy.

Holger

---

### Post by Hagar Delest on 2021-03-14
Rather weird that it cannot be opened. It has to contain very complex layout.
Can you ask someone who managed to open it to send it again to you (or as a backup a PDF export of it)?
If the file is actually NOT corrupt, then, welcome to the vendor lock-in policy and buy MS Office.
You can complain that such document should not be provided in proprietary format but rather PDF to insure equality of access.

Can you share the file so that we try?

---

### Post by HermanAB on 2021-03-14
You can try to upload and open it with Google Docs

---

### Post by TheFu on 2021-03-14
Any chance someone is trying to infect you with a file-based virus?

---

### Post by Mark Phelps on 2021-03-14
A problem you are likely to run into with MS Office files is that folks get fancy and embed stuff in them -- and when that happens, the office-equivalent apps often simply will not work.

Same is true of MS Office though -- as a file created in Office 2019 or Office 365 often can not be opened properly in older versions of MS Office.

---

