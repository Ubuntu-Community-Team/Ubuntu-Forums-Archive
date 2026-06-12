---
title: "How to convert .ppt to pdf"
date: 2013-09-18
forum: General Help
---

### Post by CkDGTAT on 2013-09-18
Hi all,

I tried libreoffice, but it doesn't work. Any other idea

```
$ libreoffice --export-to pdf *
javaldx: Could not find a Java Runtime Environment!Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx

```

Thanks

---

### Post by mikewhatever on 2013-09-18
Have you installed java?

---

### Post by slickymaster on 2013-09-18
Just type in ```
java -version
``` in a terminal window and it'll tell you what version, if any, you've got installed.

---

### Post by CkDGTAT on 2013-09-21
Anybody knows another way to convert to pdf?

---

### Post by QIII on 2013-09-21
Hello!

Did you have any success with the suggestions above?

---

### Post by tgalati4 on 2013-09-21
Open the document in LibreOffice.  Flip through all of the slides to make sure they are readable and not scrambled or otherwise mangled.  Then click Print-->Print-to-File or Print-to-PDF.  Otherwise go to File-->Export to PDF.

---

### Post by CkDGTAT on 2013-09-25
I have finally managed to use xdotool to do the recursive work.

---

