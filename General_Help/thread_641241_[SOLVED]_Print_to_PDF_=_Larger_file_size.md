---
title: "[SOLVED] Print to PDF = Larger file size"
date: 2007-12-15
forum: General Help
---

### Post by PartisanEntity on 2007-12-15
I have a 100 page PDF file, I wanted to extract some pages, so I sent a specific page range to the PDF printer.

This worked and I now have a new PDF file with the pages that I wanted. However this new file is even bigger than the original even though it has less pages?

The original PDF file was 25MB with over 100 pages, the new PDF file is about 40 pages and is 50MB in size?

The whole point was that I needed to cut the original PDF into 2-3 smaller files so I can upload them to a website.

---

### Post by niteshifter on 2007-12-15
If memory serves me correctly printing a PDF to a PDF will always make a bigger PDF - the input PDFs are treated as images.

Check out pdftk in the repositories, it will do what you need.
```
pdftk infile.pdf burst 
```
Will render your 100 page file into 100 individual files: pg_0001.pdf to pg_0100.pdf

This
```
pdftk pg_0002.pdf pg_0003.pdf pg_0004.pdf output newfile.pdf
```
takes pages 2, 3 and 4 and combines them into file newfile.pdf

But I'll wager you don't want to type 40 filenames, so let's do this since it's a block of pages:
```
pdftk infile.pdf cat 40-59 output outfile.pdf
```
will take pages 40 to 59 and combine them into file outfile.pdf

HTH

PS - Forgot to add; pdftk does other handy things as well. Check the man page on it.

---

### Post by PartisanEntity on 2007-12-15
Superb, thank you! I shall try this out.

Edit: perfect, it worked, nice and simple :)

---

### Post by niteshifter on 2007-12-15
You're most welcome, glad to help.

Hat tip to the author / maintainer of pdftk: It sure beats the heck out of my coded-in-desparation Perl scripts I made once upon a time. Thank you.

---

