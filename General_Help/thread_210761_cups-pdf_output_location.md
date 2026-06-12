---
title: "cups-pdf output location"
date: 2006-07-07
forum: General Help
---

### Post by wifiabc on 2006-07-07
Is there a way to change the name and location of the output pdf file?

---

### Post by froggay on 2006-07-13
I want to change it too !

the changelog tell [http://packages.debian.org/changelogs/pool/main/c/cups-pdf/cups-pdf_2.4.1-1/changelog]("http://packages.debian.org/changelogs/pool/main/c/cups-pdf/cups-pdf_2.4.1-1/changelog")

> - Settings are now fully configurable via /etc/cups/cups-pdf.conf

But where is it !!!
locate can' find it

---

### Post by Charles Hand on 2006-11-15
> **froggay said:**
> I want to change it too !

the changelog tell [http://packages.debian.org/changelogs/pool/main/c/cups-pdf/cups-pdf_2.4.1-1/changelog]("http://packages.debian.org/changelogs/pool/main/c/cups-pdf/cups-pdf_2.4.1-1/changelog")



But where is it !!!
locate can' find it

You don't need locate, you already know the full path:
/etc/cups/cups-pdf.conf

Edit the file using
```
sudo gedit /etc/cups/cups-pdf.conf
```

Find the line:
```
OUT ${HOME}/PDF
```

Change ${HOME}/PDF to whatever you want.

---

