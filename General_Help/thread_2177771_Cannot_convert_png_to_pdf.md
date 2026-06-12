---
title: "Cannot convert png to pdf"
date: 2013-09-30
forum: General Help
---

### Post by CkDGTAT on 2013-09-30
Hi,

Any idea about this error

```

% convert snapshot12.png snapshot12.pdfconvert: unable to open image `snapshot12.pdf':  @ error/blob.c/OpenBlob/2587.



```

---

### Post by sanderj on 2013-09-30
Works for me:

```
convert Downloads/vnstat-hallo2.png vnstatje.pdf
```

---

### Post by gordintoronto on 2013-10-01
Last resort: run LibreOffice Writer, Insert picture from file, print to PDF. You might need to install the PDF printer, which "prints" to the PDF folder in /home.

---

### Post by ac1d2 on 2013-10-01
Dont do it within linux.....

use google "convert png to pdf"

There's tons of free conversion sites out there.

---

### Post by gordintoronto on 2013-10-02
One other thought: what directory were you in at the time? Perhaps you didn't have permission to write there.

---

