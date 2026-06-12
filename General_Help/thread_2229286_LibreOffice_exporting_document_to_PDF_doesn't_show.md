---
title: "LibreOffice: exporting document to PDF doesn't show EPS images"
date: 2014-06-12
forum: General Help
---

### Post by zitelli-pablo on 2014-06-12
Hi everyone! I've been searching and a lot of people is having the same problem, but I didn't find a solution!

[B]The problem:

[/B]I have a LibreOffice document with lots of images in EPS format (the format with the best quality I could find to show MATLAB figures...), they look great. The problem comes when I export the document to PDF format: those images disappear!

[B]What I tried in LibreOffice:
[/B]
I changed all the configurations in File -> Export as PDF... and none of them makes a difference.
Instead of exporting the file, I printed it to PDF. Same issue.

**My "workaround":**

To convert all the EPS images (I saved them separatedly) to JPG, using the command 'mogrify' from ImageMagick (setting the density to 300 dpi), then replace them in the document and export to PDF. But, they are blurry in the PDF document.

Sincerely, I didn't find a solution like installing a package or something similar. I found that it also happens in Mac computers.

If any of you solved this problem, I would really thank you for sharing the solution!

I'm using Xubuntu 14.04 64 bits.

---

### Post by slickymaster on 2014-06-12
There's an old bug on that issue: [Bugzilla – Bug 34836]("https://bugs.freedesktop.org/show_bug.cgi?id=34836")

---

### Post by Impavidus on 2014-06-12
So libreoffice doesn't properly convert eps to pdf.

Eps and pdf are related file formats and are both hierarchical, in the sense that smaller eps or pdf images can be copied into larger eps resp. pdf images. So to export as pdf, all images have to be converted to pdf.

You could try converting your eps images to pdf first. This conversion is usually (almost) lossless as it stays a vector image. File size may change significantly.

---

### Post by vanadium on 2014-06-12
To have eps files rendered in high quality, you can create a PDF by "printing" to a file. However, no bookmarks and other features will be exported. In the first days of OpenOffice, before it had the export PDF command, there was a macro, ExtendedPDF, that would not only print the content to PDF, but that would also include the additional interactive features such as bookmarks. Unfortunatelly, that macro is not anymore developed.

---

### Post by vanadium on 2014-06-12
> **Impavidus said:**
> So libreoffice doesn't properly convert eps to pdf.
You could try converting your eps images to pdf first. This conversion is usually (almost) lossless as it stays a vector image. File size may change significantly.
LibreOffice unfortunatelly won't import graphics in PDF format. So this is not an option.

---

### Post by zitelli-pablo on 2014-06-12
> **vanadium said:**
> To have eps files rendered in high quality, you can create a PDF by "printing" to a file.

Thanks for your reply! I did it, but the PDF document doesn't show the EPS images either.

I'll try what impavidus says but using ImageMagick, and then post what happened.

---

