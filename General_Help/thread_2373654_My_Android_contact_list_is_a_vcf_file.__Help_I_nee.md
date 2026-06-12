---
title: "My Android contact list is a vcf file.  Help I need to print it on my desktop pc"
date: 2017-10-08
forum: General Help
---

### Post by Timmoore001 on 2017-10-08
using 16.04 ubuntu

Any thoughts anyone ?

---

### Post by howefield on 2017-10-08
Open it in any text editor and print from there ?

---

### Post by Timmoore001 on 2017-10-08
Many thanks for responding but it printed the first page and stopped.

I tried Kate and Edit

its got 354 entries so may be thats the problem...   ?

A puzzled,

Tim

---

### Post by ajgreeny on 2017-10-08
Yes, that puzzles me to, but you should be able to open it in LibreOffice writer and print from there.

I assume you can normally print multipage docs without a problem?

---

### Post by Timmoore001 on 2017-10-08
Many thanks for responding.

I used Calc and saved it as a csv file.

it printed out on A4 as 41 sheets of paper !

the 5th line was FN:name

I would love to sort the Calc file just on each 5th line,  is that possible.

I'm very ignorant on spreadsheets.... 

:  )))

Tim

---

### Post by howefield on 2017-10-11
> **Timmoore001 said:**
> ...I would love to sort the Calc file just on each 5th line,  is that possible.

I'd try loading the .csv file into Google Sheets and if looks right (might need a little work) print from there. Seems to work well enough for me.

---

### Post by efflandt on 2017-10-11
The problem with importing a VCF file with multiple contacts into LibreOffice Calc is that it generates just one column of **FIELDNAME:value** for all field names. And it does not help to add ":" as a separator because then you end up with 1 column of field names and values on separate lines. Google Sheets does not know how to import a .vcf file.

Any recommendations for a vcf editor? Much of the info I find is 5 or more years old, the most recent not modified since 2013. But looking at the file it is Vcard 2.1, so maybe some of the old programs would still work. I have a long vcf contact list from work that I need to weed out before importing into Google contacts to avoid mixing them up with ones I already added to that. 

Or alternately is there a way to generate a spreadsheet from a vcf with field names as headers across the top and field contents in appropriate columns and rows under that while eliminating the PHOTO field? That would make it easier to weed out unwanted entries by deleting rows or look up contacts. Then it would be nice to be able to export that back to a VCF file for import into an email program or gmail. If all else fails I can always open the vcf with gedit and search for names.

I used to be familiar with parsing text with Perl long ago when doing CGI scripts, but have not done that for many years and know very little python.

---

