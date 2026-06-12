---
title: "converting images"
date: 2015-03-14
forum: General Help
---

### Post by trav9595 on 2015-03-14
Is there anyway to take an image screenshot of data in columns and get it into a spreadsheet format???
Also can Office Calc save files as .txt files?  I didnt see that option in the dropdown suffix choices.....

---

### Post by Holger_Gehrke on 2015-03-14
> **trav9595 said:**
> Is there anyway to take an image screenshot of data in columns and get it into a spreadsheet format???

Yes, OCR it. I've used Tesseract at several times in the past, it's in the repositories. Be aware though: it's a command line tool, it only likes certain image file formats and it's really meant for text and can't handle tables, so you'll end up with a text file that will take quite a bit of work to turn it into a usable csv file. Might be faster to just type it in ...

> **trav9595 said:**
> 
Also can Office Calc save files as .txt files?  I didnt see that option in the dropdown suffix choices.....
csv - character separated values - is a text format. All spreadsheets know that one, both for import and export.

---

### Post by SeijiSensei on 2015-03-14
If the data is in an HTML table on a web page, you can import it directly into a spreadsheet like LibreOffice Calc from Firefox.  Carefully highlight the entire table with your mouse, including the column headers if appropriate, then right-click on a highlighted object and choose Copy.  Then Paste that into the spreadsheet. Don't know if that works with other browsers, but I wouldn't be surprised if it did.  Calc just uses the <tr><td> HTML tags to identify rows and columns.

---

