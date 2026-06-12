---
title: "[SOLVED] Cups-pdf"
date: 2007-06-22
forum: General Help
---

### Post by rolodoom on 2007-06-22
I'm using CUPS-PDF to create pdf files. Everything is working like a charm (I follow this instructions [http://www.linux.com/articles/61826]("http://www.linux.com/articles/61826")), but I don't know how to change the default output folder for the final pdf, the all are being created at a PDF folder at my home dir.

any suggestion???

---

### Post by Brucevdk on 2007-06-22
Take a look at */etc/cups/cups-pdf.conf*.

[PHP]
### Key: Out
##  CUPS-PDF output directory 
##  special qualifiers: 
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf/${USER}

Out ${HOME}/PDF
[/PHP]

---

### Post by dbott67 on 2007-06-22
Here's a HOWTO I wrote a while ago on printing to PDF.  As Brucevdk points out, you just need to edit the cups-pdf.conf file.  More specific details in this thread:

[http://ubuntuforums.org/showthread.php?t=283198](http://ubuntuforums.org/showthread.php?t=283198)

-Dave

---

### Post by TheTinman on 2007-07-07
Have you noticed that when printing in Firefox with cups-pdf or the native PostScript creator the resulting text is not highlight-able/selectable when viewing the file with Evince?

---

