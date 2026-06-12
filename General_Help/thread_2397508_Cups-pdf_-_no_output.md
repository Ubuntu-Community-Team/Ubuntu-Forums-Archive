---
title: "Cups-pdf - no output"
date: 2018-07-30
forum: General Help
---

### Post by alansecker on 2018-07-30
On a clean install of 18.04, I have been running up all those applications and drivers necessary to support my weird needs. The last sticking point is cups-pdf.

I installed printer-driver-cups via synaptic, edited cups-pdf.conf so that 'Out' pointed to where I wanted the pdf files.

Later on I did the following based on a thread in: 
[https://ubuntuforums.org/showthread.php?t=1313291](https://ubuntuforums.org/showthread.php?t=1313291)
because I had had an 'insecure filter' message. This cured it:

$ sudo chown -hR root /usr/lib/cups/filter
$ sudo chown -hR root /usr/lib/cups/backend
$ sudo chgrp -hR root /usr/lib/cups/filter
$ sudo chgrp -hR root /usr/lib/cups/backend 

Yet I cannot see or find any output files.

---

### Post by ajgreeny on 2018-07-30
Do you really need printer-driver-cups-pdf on your machine to support those weird needs of yours?

I have never had that package installed in my 13 years of running Ubuntu or Xubuntu but I do still print a lot of PDF files from many and varied applications simply by choosing "Print to file" from the print dialogue, then in that choose PDF and edit the specific settings if you need to. You can change the filename and pathway of the output file in the print dialogue to whatever you want.

---

