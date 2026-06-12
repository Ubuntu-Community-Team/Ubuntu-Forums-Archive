---
title: "How do I print a PDF file?"
date: 2007-08-10
forum: General Help
---

### Post by ross9885 on 2007-08-10
I am trying to print a government form in pdf format, and I am having the following problems:
[LIST]
[*]ePDF and xPDF don't give me the option of printing at all
[*]The adobe reader won't start, trying to right click on a pdf and select 'Open With "Adobe Reader"' does nothing, not even an error.
[*]pdf2ps does give me a printable .ps file, but it alters the document so much that I am worried the government or their machines might not accept it.
[/LIST]
All searches for printing a pdf in Ubuntu lead to info on how to print TO a pdf, not from pdf to paper.
Thank you for your time.

---

### Post by davidv64 on 2007-08-10
Did you try evince? It works (and prints) fine for me.

---

### Post by ross9885 on 2007-08-10
Works for me too, thanks.

---

### Post by chaotik on 2007-09-30
I am still struggling with this issue.  

I was not able to print a pdf file to my networked Dell color printer, but am able to print a pdf file to other network printers.  This Dell printer will print fine from Open Office, and will print a test page without a problem.  

I was finally able to get it to print the pdf file only by using Evince to open the file and then use the "print to pdf" file option.  Then, when I opened this newly created pdf file with Evince, I was able to successfully print it to my networked Dell printer.   

I view this as a temporary work-around, and am still looking for a solution.  Does anyone have any other suggestions?

Thanks!

---

### Post by Brian96 on 2007-09-30
> **chaotik said:**
> I am still struggling with this issue.  

I was not able to print a pdf file to my networked Dell color printer, but am able to print a pdf file to other network printers.  This Dell printer will print fine from Open Office, and will print a test page without a problem.  

I was finally able to get it to print the pdf file only by using Evince to open the file and then use the "print to pdf" file option.  Then, when I opened this newly created pdf file with Evince, I was able to successfully print it to my networked Dell printer.   

I view this as a temporary work-around, and am still looking for a solution.  Does anyone have any other suggestions?

Thanks!

I have the same problem with the same parameters, except that the workaround you describe did not work for me. I, too would appreciate input.

Is it possible that the solution lies in the printer drivers or printer settings? Evince shows my printer, but does not enable the "Print" button for it.

---

### Post by gcordoba on 2007-10-01
Brian, usually in Evience the print button does not appear if there is not an opened document.

By  the way, I am trying to print a PDF using Acrobat reader. However, it use a command line order like lp or lpr. At least in my Dapper, it seems that that single command line is not enough. Please, any of you have an idea about the options need to print in Dapper through command line? 

Thanks,
Gustavo

PS: Dell printers are a nightmare in Linux

---

