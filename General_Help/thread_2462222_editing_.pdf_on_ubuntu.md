---
title: "editing .pdf on ubuntu"
date: 2021-05-16
forum: General Help
---

### Post by jvglynnjr on 2021-05-16
None of the .pdf editors I have tried seem to be capable of what I need. LibreOffice Draw, Okular,  and Inkscape have not worked out. Google Docs completely messes up the formatting. 


I have a .pdf that I need to edit. I have been able to edit some text with LibreOffice Draw, but I can't figure out how to fix bad page breaks. Is there a .pdf editor available for Linux that can do this? Or is there a way to reliably convert a .pdf to a word processor format?

---

### Post by HermanAB on 2021-05-16
I normally use Gimp, Xournal and PDFshuffler.  Between those 3 one can do pretty much anything.

---

### Post by Impavidus on 2021-05-16
I can't rule out that you can find a tool that by sheer luck does exactly what you want, but it's not likely to happen. PDF was never designed to be editable; it was designed to be send to printers. You edit the file from which the pdf was generated, then regenerate the pdf. The person who created your pdf did a bad job.

To solve this, you have to undo the conversion from whatever the source was to pdf, change the page breaks and reconvert to pdf. But during the conversion to pdf, information is lost, like all logical structure and layout hints, as only the actual layout is stored in the pdf. Therefore this back conversion needs guesswork, which rarely works well.

---

### Post by dragonfly41 on 2021-05-16
Foxit might be worth looking at.

[https://www.foxitsoftware.com/blog/how-to-edit-a-pdf-document/](https://www.foxitsoftware.com/blog/how-to-edit-a-pdf-document/)

---

