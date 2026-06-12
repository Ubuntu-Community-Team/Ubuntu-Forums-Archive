---
title: "LibreOffice - can't insert image"
date: 2021-09-13
forum: General Help
---

### Post by nikkkko on 2021-09-13
Hi,

I recently re-installed Ubuntu 20.04.3 LTS after a long absence and am struggling with a couple of things, one of them being the inability to insert an image into a document.  LibreOffice, which I installed from the Ubuntu Software GUI,  gives the error message, "Image filter not found" .  Any pointers in the right direction would be much appreciated.

Nick

---

### Post by Impavidus on 2021-09-13
The error message suggests (but I have to say I rarely use libreoffice) that libreoffice doesn't know how to handle the image file format.

---

### Post by nikkkko on 2021-09-13
Yes, and I am wondering how to rectify that.  I have used LO for many years and this is the first time it ever refused to insert an image.

---

### Post by Impavidus on 2021-09-13
So, what file format is it? Something standard like png or some exotic format? And some formats come in different versions or have some optional features, not supported by all viewers. The **file** tool may tell more specifics about the format:```
file /path/to/file
```
Have you tried using some image editing program to open the file, then save it again in a different format (or a different version of the same format)?

---

### Post by nikkkko on 2021-09-13
The file is plain vanilla .jpg. There's something missing in my install - I installed the Libre Writer only app from Ubuntu Software and that works and would be fine if it weren't an ancient version - looks like Win95.

---

