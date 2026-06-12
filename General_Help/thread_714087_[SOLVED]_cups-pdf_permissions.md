---
title: "[SOLVED] cups-pdf permissions"
date: 2008-03-03
forum: General Help
---

### Post by cmnorton on 2008-03-03
I am missing something obvious in setting up CUPS-pdf. I have it working on Ubuntu  on two other systems. I have set up a third system -- all three are 7.10 -- and looked at /etc/cups/cups-pdf.conf on the third system. cups-pdf does not work on the third system.

I can see directory activity (date stamps) in /var/spool/cups-pdf, but no pdf files show up.

These are errors in
/var/log/cups/cups-pdf_log

Mon Mar  3 13:04:29 2008  [ERROR] failed to create directory (/var/spool/cups&#8722;pdf)
Mon Mar  3 13:04:29 2008  [ERROR] failed to create user output directory (/var/spool/cups&#8722;pdf/cnorton)

Here are the directory permissions:

drwxr-xr-x 2 root root 4096 2008-03-03 13:03 cnorton
drwxr-xr-x 2 root root 4096 2008-03-03 13:07 SPOOL
r

This is in the error log under cups:

E [03/Mar/2008:13:02:38 -0500] PID 7295 (/usr/lib/cups/backend/cups-pdf) stopped with status 255!

Any ideas?

---

### Post by cmnorton on 2008-03-04
I found the problem. I thought the cups-pdf installation had not created the printer, but it had. I created a second printer, and the two PDF printers conflicted. The log files actually showed the pdf file being deleted right after it was created.

As far as the cups-pdf install for 7.10 goes, it has improved so much, that I am leaving the defaults as is and taking my PDFs right out of the PDF directory created under my home directory by the install. It beats tweaking the /var/spool directory's permissions.

---

