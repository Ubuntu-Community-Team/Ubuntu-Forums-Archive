---
title: "Problem to convert .pdf to .jpg"
date: 2022-04-30
forum: General Help
---

### Post by satimis on 2022-04-30
Problem to convert .pdf to .jpg

$ convert Reynold_new.pdf Reynold_new.jpg```

convert-im6.q16: attempt to perform an operation not allowed by the security policy `PDF' @ error/constitute.c/IsCoderAuthorized/408.
convert-im6.q16: no images defined `Reynold_new.jpg' @ error/convert.c/ConvertImageCommand/3258.

```

Reynold_new.pdf can be opened in Libre Office and Document Viewer

Pls advise.  Thanks

Regards

---

### Post by norobro on 2022-04-30
Lots of hits if you search for that error.

This one worked for me: [https://fluca1978.github.io/2020/06/03/ImageMagikPDF.html](https://fluca1978.github.io/2020/06/03/ImageMagikPDF.html)

---

### Post by #&amp;thj^% on 2022-04-30
along with norobro's suggestion: [https://stackoverflow.com/questions/43085889/how-to-convert-a-pdf-into-jpg-with-command-line-in-linux](https://stackoverflow.com/questions/43085889/how-to-convert-a-pdf-into-jpg-with-command-line-in-linux)

---

### Post by satimis on 2022-04-30
Hi all,

Following command line works for me;

pdftoppm -jpeg -r 300 input.pdf output

Thanks

Regards

---

