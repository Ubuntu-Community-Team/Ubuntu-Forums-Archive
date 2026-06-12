---
title: "Evince for editing PDF files"
date: 2020-05-18
forum: General Help
---

### Post by acefromspace on 2020-05-18
I'm using Ubuntu 16.04 and want to download Evince to edit PDF files (does it edit or is it just a reader?)
I can already read PDF files but can't do anything else.
Also, which version of Evince do I download? Computer is an older Dell inspiration

---

### Post by TheFu on 2020-05-18
Evince is a reader last time i checked.

Xournal or LibreOffice can export to PDF.  PDF cannot be edited, except to add annotations.

The process with Xournal is to read to existing PDF, modify it in RAM, then save (export to PDF) to a different PDF filename. Xournal also keeps annotations in a separate file, so both the annotations and PDF file need to be moved together to keep access to the annotations.

There are $30-$70 commercial PDF tools that work with newer PDF file standards. These are not from Adobe, which is more expensive and more comprehensive.  Initially, PDF creation was accomplished via a printer driver from Adobe.  We'd "print" PDF files. I don't recall how Adobe handled annotations, just that where I've worked and coded for PDF workflows, we kept annotations separate and overlaid the requested annotation from the document author, then the user's group(s), then the user, in that order.

Most of the F/LOSS tools are still using v1.6 of the PDF standard.  Adobe wants to keep making money, so they add tiny features and bump up the current PDF standard so people, govts, and businesses have to buy new PDF creation software or the competition has to re-engineer the published file format changes into their new software.  At least Adobe works with a published standard for the PDF files and has versioning, unlike, cough, many other companies with very popular data file formats still used as a paid-walled-garden for 100% compatibility. Enough SW politics.

---

### Post by Dennis N on 2020-05-18
Evince: You can add annotations (an icon that opens a note in a separate small window), and add highlighting to text, but you  can't change existing content.

---

### Post by GhX6GZMB on 2020-05-18
There's very little you can do with PDFs. As others said, you can add annotations and in some cases delete text. That's about it.
PDF is not designed for editing, but as "digital paper", that's the reason for its popularity, people trust PDFs.

---

### Post by Eduardoecp on 2020-06-13
In my opinion, PDF Editor is the best open-source app to edit PDFS. You can, for example, write your test on a PDF file, or highlight the text that is already in the file. 

You can get the deb from the official site: [https://sourceforge.net/projects/pdfedit/](https://sourceforge.net/projects/pdfedit/)

You may be unable to install it because some new versions of Ubuntu don't have the dependencies. There is a workaround [here]("https://scriptips.org/2020/06/02/pdfeditor/").

---

### Post by dragonfly41 on 2020-06-13
Try Foxit reader .. it has a number of annotation features.

---

### Post by monkeybrain20122 on 2020-06-14
What do you want to do with the PDF file? Many PDF readers can add annotations, evince, qpdfview, okuar... If you want to split, stable, rearrange pdf files then there is pdfshuffler in the repo. If you want to edit the content there is the [master]("https://code-industry.net/free-pdf-editor/") pdf editor (both free and paid versions available)

---

