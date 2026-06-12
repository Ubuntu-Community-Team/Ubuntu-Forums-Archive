---
title: "Package cups-pdf (12.04) default file naming"
date: 2013-05-07
forum: General Help
---

### Post by timothylegg on 2013-05-07
Hello,

I have two machines one phase-out machine with Ubuntu 10.10 and a new Apple with Ubuntu 12.04 running parallels

In my work, I am forced to print from Flash applications and need a PDF printer installed.  On my old machine, I followed a set of instructions that worked beautifully for me, but not sure exactly the blog I read to set this up.  Similarly, I sought to set this up on my 12.04 instance.  I installed cups-pdf and it works well for me.

I ran into problems with the file naming scheme.


On the 10.10 machine, the files are put in~/PDF/ and the file name has a template of job_%d_-untitled_document.pdf where %d is an integer (now in the thousands) that automatically increments each time I print from this Flash application.  It's impossible to overwrite a document without deliberately tampering with file names.

On the 12.12 machine, I get a default file name of _stdin_.pdf, which is overwritten if I were to be so careless as to not rename the file after printing the prior print job.  I would like a unique, sequential file naming scheme.

So how would I go about this?  Fortunately, I have a machine that has this feature.  This entry was originally created to be a question, but when I went to enter the tags for the message, cups-pdf.conf autocompleted (thank you UbuntuForums.com).  I stopped everything I was doing to search for the files and compared them.  

The two files in /etc/cups/cups-pdf.conf were very similar. Of the 4 or 5 daemon-readable lines, one of them was

Label 0

On the 10.10 machine, it was active in this form, on 12.12, it was commented out.  I made the change, but the result was still the same.  Reading the comments in the file, I changed the '0' to a '1'.  So now I have

Label 1

The problem was solved.  I now have unique file names when printing to PDF.  The files are named ~/PDF/job_%d-_stdin_.pdf where the job number is still in the single digits.

Maybe somebody can chime in about where the text "_stdin_.pdf" and "untitled_document.pdf" is stored...

Timothy D. Legg

---

