---
title: "Cannot open .pdf in Evince or any other pdf viewer, please help!"
date: 2016-09-27
forum: General Help
---

### Post by waylae on 2016-09-27
Hi guys,

I have tried multiple times to open .pdf's using Evince, Qpdfviwer and Xpdf and I cannot manage to open a .pdf file in any of these programs. I have re-downloaded the .pdf's even tried different ones all together... I have done a google search and couldnt find an answer, any help will be appreciated.

---

### Post by howefield on 2016-09-27
Link to the .pdf file if publicly available ?

---

### Post by waylae on 2016-09-27
[https://www.humanservices.gov.au/sites/default/files/documents/su001-1508en.pdf](https://www.humanservices.gov.au/sites/default/files/documents/su001-1508en.pdf) 
&
[https://www.humanservices.gov.au/sites/default/files/modia-1602en.pdf](https://www.humanservices.gov.au/sites/default/files/modia-1602en.pdf)

---

### Post by howefield on 2016-09-27
Tried both successfully,  viewed in browser, then downloaded and opened with Evince albeit with vanilla Ubuntu 16.04.1.

Which version of Lubuntu are you using ?

---

### Post by waylae on 2016-09-27
Yeah I wouldn't have thought it would be the files themselves. I am using Lubuntu 16.04.1

---

### Post by howefield on 2016-09-27
Tried both in Lubuntu 16.04.1 and no problem in opening.

Do you get any error(s) if you try to open one of the pdf files via the terminal ?

```
evince /path/to/file.pdf
```

---

### Post by waylae on 2016-09-27
I get the following error:

** (evince:8063): WARNING **: Error retrieving accessibility bus address: org.freedesktop.DBus.Error.ServiceUnknown: The name org.a11y.Bus was not provided by any .service files

---

### Post by kalehrl on 2016-09-27
Install at-spi2-core

---

### Post by waylae on 2016-09-27
Ok I ran:

sudo apt-get install at-spi2-core

and it installed correctly, though when I run:

evince /path/to/file.pdf

I get the following error:
Bus error (core dumped)

and when I try to open the pdf normally, the document viewer opens but shuts down before displaying anything.

---

### Post by howefield on 2016-09-27
How about right clicking the pdf file and selecting "*open with other application*" > view all applications and select Firefox, does it open then (within a browser window).

---

### Post by vasa1 on 2016-09-27
> **waylae said:**
> Yeah I wouldn't have thought it would be the files themselves. I am using Lubuntu 16.04.1
Is this a vanilla Lubuntu 16.04 or is it an upgrade?
Do other applications work well?
If you have Firefox or Google Chrome, can you view pdf files using their built-in pdf viewers?
Do you have dbus-x11 installed?

---

