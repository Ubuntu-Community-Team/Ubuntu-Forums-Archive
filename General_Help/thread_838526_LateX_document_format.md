---
title: "LateX document format"
date: 2008-06-23
forum: General Help
---

### Post by X-dark on 2008-06-23
Hello,
I try to do a LateX document with the songbook package. I've added this : ```
\documentclass[a5paper]{book}
``` to generate an A5 document.
But the pdf generated is A4 with text formated in A5.
How do I generate the pdf in A4 ?

I use gedit with the latex plugin to compile the tex file.

I also doesn't succeed to generate a TOC.

---

### Post by dvase on 2008-06-23
> **X-dark said:**
> Hello,
I try to do a LateX document with the songbook package. I've added this : ```
\documentclass[a5paper]{book}
``` to generate an A5 document.
But the pdf generated is A4 with text formated in A5.
How do I generate the pdf in A4 ?

I use gedit with the latex plugin to compile the tex file.

I also doesn't succeed to generate a TOC.

What sort of build settings are you using (e.g., DVI, PDF)?

Additionally, [this page]("http://www.tex.ac.uk/cgi-bin/texfaq2html?label=papergeom") may be of help.

---

### Post by X-dark on 2008-06-24
I've tried both dvi and pdf, but I'm interrested for a PDF.
I use the gedit LateX plugin so everythin is handled automatically by rubber. The command issued is : ```
rubber -f -s --inplace -d <the_tex_file>
```
I've noticed the issue is not specific to songbook package. With a standard book document class the problem is the same.

---

### Post by X-dark on 2008-06-24
problem solved with /pdfpageheight and /pdfpagewidth macro.
Thank you.

I've still the TOC/index issue.

---

### Post by dvase on 2008-06-24
> problem solved with /pdfpageheight and /pdfpagewidth macro.

Glad to hear that.

> 
I've still the TOC/index issue.

I'm a little confused by the TOC/index issue, would you like a TOC in the document text (e.g., after the title)? Or an index of bookmarks in the PDF document?

Additionally, the example you attached doesn't include any \chapter, \section, etc. commands which required to demarcate TOC points.

---

### Post by X-dark on 2008-06-24
> **dvase said:**
> 
I'm a little confused by the TOC/index issue, would you like a TOC in the document text (e.g., after the title)? Or an index of bookmarks in the PDF document?

Additionally, the example you attached doesn't include any \chapter, \section, etc. commands which required to demarcate TOC points.

yep, I want to add a TOC after the title. The example I provided is bad for that, but I've don't have the right tex file on my pc right now. I'll upload it for you to see.
In this one when I compile the toc file is generated but nothing is added to the result.

---

