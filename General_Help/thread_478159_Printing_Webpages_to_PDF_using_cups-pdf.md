---
title: "Printing Webpages to PDF using cups-pdf"
date: 2007-06-19
forum: General Help
---

### Post by willl69 on 2007-06-19
Hi All,

Just wondering if anybody knows of a way to print a webpage to a pdf using cups-pdf from the command line?  I need to print to pdf on a remote ubuntu server if i can, just wondering if it is possible this way or if anybody knows of another way it can be achieved. 

Cheers

Will

---

### Post by beatbros on 2007-06-19
Hi,
there is a Perl Module and some script already written.


Take a look here, maybe it is useful:

[http://linux.softpedia.com/get/Programming/Libraries/PDF-FromHTML-16198.shtml](http://linux.softpedia.com/get/Programming/Libraries/PDF-FromHTML-16198.shtml)

Once you get the pdf you can print it directly to cups

bye

---

### Post by willl69 on 2007-06-19
Thanks for that suggestion

I was more wondering if cups-pdf could be used to create the pdf as a browser such as firefox sees it, but from the command line.  I have tried this script and a few others like it it is a little bit of a blunt tool when converting  complex web pages.  Just looking for a way to get the quality of a browser print in PDF form, that is, if it is possible.

Cheers

Will

---

### Post by beatbros on 2007-06-19
Ah... ok. 
After further reading on, i've not found something useful and easy-fitting to your needs.
Could be interesting, however,  to keep info in this thread if something new comes out and it works also in complex web pages/documents.

Bye

---

### Post by willl69 on 2007-06-19
If anybody knows of a way do do this sort of thing but convert the HTML accurately into a PostScript or image file, that would also be very useful

Cheers

Will

---

### Post by wyth on 2007-06-28
Can't speak for your setup, but CUPS came with a default "Print to PS" option.  

I just saved 12 web pages to postscript by going to the pages (in firefox), and:

[LIST]
[*] ctrl-p (print)
[*]Printer Name: (drop-down menu) PostScript/default
[*]ticked the Print to File box
[*]click Print
[*]then asked where to save and what to name the file.  When done, you have a postscript file of the webpage.[/LIST]

---

### Post by willl69 on 2007-07-04
I know the pdf and postsript can be done with cups, but my problem is i need to automate it via command line.  

Ive found this that seems pretty effective in converting html to ps and pdf, but it is kinda slow for large pdfs and a bit resource greedy:

[http://www.tufat.com/script19.htm](http://www.tufat.com/script19.htm)

Thanks for your reply.

Cheers

Will

---

### Post by riger99 on 2007-08-11
Hi, you could try this: [http://ubuntulinuxhelp.com/easy-pdf-creation-in-ubuntu-linux/]("http://ubuntulinuxhelp.com/easy-pdf-creation-in-ubuntu-linux/")
It shows you a VERY fast way to install and use.
Maybe it'll help you too?
I hope so.

---

