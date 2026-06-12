---
title: "importing csv files"
date: 2015-03-12
forum: General Help
---

### Post by trav9595 on 2015-03-12
some of the tax software sites let you import csv files instead of manually entering long lists of text. When Ubuntu asks to save a csv file it asks you to
confirm that you want it to save csv and not odt. I save it to csv but the tax software wont take it. I get a message that says ..this doesnt seem to be a simple text file....or something like that. Does anyone know how to arrange the data so it will be accepted by TaxAct..??

---

### Post by SeijiSensei on 2015-03-12
Do you save the file with a .csv extension?  Are you using the defaults in calc?  Can TaxCut import any other formats like Excel?  If so, try saving from calc to that instead of CSV.

---

### Post by bab1 on 2015-03-12
> **trav9595 said:**
> some of the tax software sites let you import csv files instead of manually entering long lists of text. When Ubuntu asks to save a csv file it asks you to
confirm that you want it to save csv and not odt. I save it to csv but the tax software wont take it. I get a message that says ..this doesnt seem to be a simple text file....or something like that. Does anyone know how to arrange the data so it will be accepted by TaxAct..??

A csv file is a text formatted file by definition.  I have created csv files with a text editor and used LO Calc to read them later.  Any text editor can open and/or create a Comma Separated Value file as well as LO Calc.  Did you include a row that defines each column at the top?  What does your file look like when you open it in a text editor?  Post the first 3 rows so we can see the formatting. 

Looking at the help provided by TaxAct themselves at [http://www.taxact.com/support/881/how-to-import-stock-information-using-a-csv-file-from-your-broker/]("http://www.taxact.com/support/881/how-to-import-stock-information-using-a-csv-file-from-your-broker/") tells me that the default Comma Separated Value (csv) is used.

---

### Post by SeijiSensei on 2015-03-12
duplicate post deleted

---

### Post by SeijiSensei on 2015-03-12
> **trav9595 said:**
> I get a message that says ..this doesnt seem to be a simple text file....or something like that.

I'm wondering if TaxAct expects the file to have DOS/Windows style end of line markers, the ones that contain both a "carriage return" and a "line feed" character rather than just the return character Unix uses.  If so, then a file without linefeeds will look like a binary file rather than a text file.  

I suggest trav9595 install the **tofrodos** package and try running the command:
```
todos < /path/to/file.csv > /path/to/newfile.csv
```
which will add the linefeeds and save the result as newfile.csv.  See if TaxAct likes that version any better.

---

### Post by vasa1 on 2015-03-12
> **trav9595 said:**
> some of the tax software sites let you import csv files instead of manually entering long lists of text. When Ubuntu asks to save a csv file it asks you to
confirm that you want it to save csv and not odt. I save it to csv but the tax software wont take it. I get a message that says ..this doesnt seem to be a simple text file....or something like that. Does anyone know how to arrange the data so it will be accepted by TaxAct..??
I don't know about TaxAct at all but the way I'd make a csv file is to use LibreOffice Calc. 
I enter my data there and not in LibreOffice Writer or anything else. 
First, save the data in the default ODF format suggested by LO Calc: that will have .ods (not .odt) as the file suffix. 
Make sure the file is proper: all figures should actually be figures and not text: such things can happen when copy/pasting data from the web. There shouldn't be any rogue spaces or other characters. Obviously, commas are a no-no.
Then, using LibreOffice Calc, save the file as CSV. You'll get a screen with various self-explanatory options. Such a file should be a plain text file as bab1 pointed out. It may not look pretty in a text editor. But you should be able to right-click on the file in your file manager (or on your desktop) and choose open with LibreOffice Calc. Again, you'll get various options and a preview of what your file will look like.

Bottom line: I'd make a csv file using Calc rather than a non-spreadsheet program (because you mentioned .odt which is the default format of Writer).

---

