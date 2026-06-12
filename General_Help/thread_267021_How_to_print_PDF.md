---
title: "How to print PDF?"
date: 2006-09-28
forum: General Help
---

### Post by dema on 2006-09-28
How can I print to a PDF-file with Ubuntu?

---

### Post by JoshHendo on 2006-09-28
cups-pdf:
[http://ubuntuos.com/2006/03/howto-set-up-a-pdf-printer](http://ubuntuos.com/2006/03/howto-set-up-a-pdf-printer)

---

### Post by dema on 2006-09-28
Well, the line "RunAsUser Yes" dont excist in the file :(  So I just added "RunAsUser No" to the top of the file..
But "PDF Printer" are not detected in "new printer".

---

### Post by Aldino on 2006-09-29
I have same problem as above described, thanks in advance for a hand:-))) Aldo

---

### Post by sa87 on 2006-10-03
I tried the initial idea and got nowhere like the repliers, then found the following elsewhere that works perfectly....

From: [http://brianpedigo.info/print_pdf_files_from_any_app_in_ubuntu](http://brianpedigo.info/print_pdf_files_from_any_app_in_ubuntu)


> You can PRINT PDFs FROM ANY APP IN UBUNTU by doing the following:

From Terminal type: sudo apt-get install cups-pdf
and then: sudo chmod +s /usr/lib/cups/backend/cups-pdf

Now go to:

System -> Administration -> Printing
New Printer
Add a Printer
Select Local PDF Printer, Next
Generic Manufacturer
Choose “postscript color printer rev3b”
apply

Printouts go to your home/PDF directory unless you edit:

/etc/cups/cups-pdf.conf

### Key: Out
## CUPS-PDF output directory
## special qualifiers:
## ${HOME} will be expanded to the user’s home directory
## ${USER} will be expanded to the user name
## in case it is an NFS export make sure it is exported without
## root_squash!
### Default: /var/spool/cups-pdf/${USER}

Out ${HOME}/PDF/

I did notice that the PDF printer was immediately recognised as a printer after I chmod'd /usr/lib/cups/backend/cups-pdf

---

### Post by th0mas on 2006-10-19
hi,

that works perfectly, thanks for the tip :)

if someone ever hear about a project such as [PDF Creator]("http://sourceforge.net/projects/pdfcreator/") for Linux, just post the url !

i wish this "print as pdf" was implemented in the next ubuntu

---

### Post by FrankVdb on 2006-10-20
Yeah, would be nice to have this as a standard feature. Will Windows Vista have this? If not, this could make another difference...

---

### Post by mph66 on 2006-10-24
Hi All, 

This method of setting up printing works exactly as others have reported.  I'm still pretty new to Ubuntu, however, and I'm used to Mac's Print to PDF feature, whereby, upon choosing, "Save As .pdf" the user is greeted with a dialog box asking him where to save.  I'd like this same functionality, rather than having to designate one specific place to save the file (by default, the home directory).

Is there any way someone can help me edit the .conf file so that choosing the PDF print option brings up the save dialog?  Right now, I can click "Print to File" in the dialog, but that saves as postscript. I need to save to .pdf so that the file format remains universal between platforms.

Thanks,

Marc

---

