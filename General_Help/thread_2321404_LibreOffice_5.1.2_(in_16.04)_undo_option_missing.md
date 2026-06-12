---
title: "LibreOffice 5.1.2 (in 16.04): undo option missing?"
date: 2016-04-22
forum: General Help
---

### Post by vasa1 on 2016-04-22
In older versions of LibreOffice, one could set the number of "undo" steps. I'm not seeing that in the LibreOffice version from the stock repo. (*I installed only Calc and Writer and not the entire suite.*)
```
06:46 PM ~ $ apt-cache policy libreoffice-calc
libreoffice-calc:
  Installed: 1:5.1.2-0ubuntu1
  Candidate: 1:5.1.2-0ubuntu1
  Version table:
 *** 1:5.1.2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
06:46 PM ~ $ apt-cache policy libreoffice-writer
libreoffice-writer:
  Installed: 1:5.1.2-0ubuntu1
  Candidate: 1:5.1.2-0ubuntu1
  Version table:
 *** 1:5.1.2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
06:46 PM ~ $ 
```

I've attached an image of the relevant help page and an image of what I see in Tools > Options > LibreOffice > Memory

Edit: I typed 1-60 one number to a cell of a spreadsheet and could undo them all.

---

