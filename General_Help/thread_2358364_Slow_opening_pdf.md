---
title: "Slow opening pdf"
date: 2017-04-12
forum: General Help
---

### Post by raleigh3 on 2017-04-12
LibreOffice is trying to open a 6 mb pdf file.

It's been 5 mins and it still is not open.

Is that normal ?

---

### Post by Autodave on 2017-04-12
Nope.  Corrupted file perhaps?

---

### Post by vasa1 on 2017-04-12
Why are you not using Evince aka Document Viewer to view your pdfs?

---

### Post by Autodave on 2017-04-12
Try rebooting machine and see what happens. Can you open the file on any other machine?

---

### Post by ajgreeny on 2017-04-12
What does the command ```
file /path/to/file.pdf
``` tell you about the file and its pdf version?

---

### Post by raleigh3 on 2017-04-12
> **vasa1 said:**
> Why are you not using Evince aka Document Viewer to view your pdfs?

I switched to Evince.

It opens pdfs much faster.

> **ajgreeny said:**
> What does the command ```
file /path/to/file.pdf
``` tell you about the file and its pdf version?

I get PDF document, version 1.6

---

### Post by vasa1 on 2017-04-12
> **raleigh3 said:**
> I switched to Evince.

It opens pdfs much faster.
Opening a pdf file in LibreOffice would involve the *Draw* component of the suite. That may be useful if one wants to do some sort of editing: from 2012 ... [Edit PDF documents with LibreOffice Draw]("http://www.techrepublic.com/blog/tr-dojo/edit-pdf-documents-with-libreoffice-draw/")

---

### Post by raleigh3 on 2017-04-13
That probably explains why it was so slow.

The document was for a cell phone and had lots of pictures.

---

