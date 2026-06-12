---
title: "[SOLVED] cups-pdf, no files, but no errors"
date: 2007-08-30
forum: General Help
---

### Post by cmnorton on 2007-08-30
Bearing in mind there are quite a few cups-pdf posts, I have looked at other posts covering cups-pdf, and did not find something similar, so here goes. 

I have installed cups-pdf on 6.06 LTS. The install did not provide me an /etc/cups/cups-pdf.conf file, so I took a working conf file from another system, where cups-pdf works.

My access and page logs look okay. There is nothing in the error log. However, there is no PDF file. I also configured cups-pdf.conf, so there is a user directory in /var/spool/cups-pdf.

I also downloaded and built from source and followed those instructions as well.

I would appreciate any pointers on what to look for next.

Thanks.
cmn

---

### Post by Total_Biscuit on 2007-08-30
Did you read this thread when looking for solutions to your problem: [http://ubuntuforums.org/showthread.php?t=188860](http://ubuntuforums.org/showthread.php?t=188860) ?  To be honest, I've been using cups-pdf since dapper and never had any problems.  Once it's set up a "PDF" directory will be created in your home directory for the output.

---

### Post by cmnorton on 2007-08-30
Thank you for referencing that post; I had not seen it.

The sudo command referenced in the post

sudo chmod 4755 /usr/lib/cups/backend/cups-pdf

did the trick. I now have a pdf document.

Thank you again.
cmn

---

