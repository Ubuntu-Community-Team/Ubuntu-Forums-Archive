---
title: "OCR to pdf"
date: 2024-01-03
forum: General Help
---

### Post by hakelm on 2024-01-03
I have a Windows 10 virtual VM-ware guest on my Ubuntu 22.04 taking up about 50 GB disk space.
This for the single purpose of an OCR program ABBYY FineReader 9.0 Sprint that many years ago came along with a printer I bought.
This program flawlessly scans, OCRs and converts the images to pdf files.
I have tried to use tesseract but it can only produce text files and I haven't managed to install ABBYY FineReader under wine.
Is there any addon to tesseract or other linux program that can produce pdf files similar to ABBYY FineReader?
Thanks for any tip
hakelm

---

### Post by readableauthor on 2024-01-03
Could you give an example of source and result files? I've never used FineReader before

---

### Post by ActionParsnip on 2024-01-03
Seems to just be OCR (Scan document and make editable text file). Is this correct please?

---

### Post by ActionParsnip on 2024-01-03
If so then gscan2pdf may be what you need

---

### Post by hakelm on 2024-01-03
Thanks. I hadn't heard about gscan2pdf. Sadly it falls far short of the at least 9 years old ABBY. Please see the examples I prepared on
[https://smeden.org/scan2pdf/](https://smeden.org/scan2pdf/) (the gscan2pdf was to large to attach). I haven't done anything to optimise the settings of any of the programs. The textfiles where extracted with pdftotext If someone is interested I can prepare more samples.
I got the ABBY program as a bonus when I bought an Epson printer 2014.
Hakelm

---

### Post by dragonfly41 on 2024-01-03
I wonder if [Scribus]("https://sourceforge.net/projects/scribus/") might fit the bill. There are imageframes and textframes in the page layout. Output is PDF ready for print.
It is not clear to me if you expect to extract text for analysis.

---

### Post by SeijiSensei on 2024-01-03
What file format does the scanner use natively? TIFF? You can try tiff2pdf on that.

[https://linux.die.net/man/1/tiff2pdf](https://linux.die.net/man/1/tiff2pdf)

---

