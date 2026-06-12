---
title: "How to convert pdf to jpg?"
date: 2018-08-26
forum: General Help
---

### Post by afters on 2018-08-26
How to convert pdf to jpg?

---

### Post by NM5TF on 2018-08-26
> **afters said:**
> How to convert pdf to jpg?

open the pdf file with your Office (Open Office or Libre Office) app.....

top left menu bar go to File > Export

drop down Export menu select jpg

try it.....

tommy

---

### Post by pqwoerituytrueiwoq on 2018-08-26
You can also use Gimp (I tend to use this to edit pdf files)
If you would prefer the command line ($width is the desired with of the jpg in pixels)
```
convert input.pdf -resize $width output.jpg
```
If the pdf is more than one page you will have multiple output files (output-0.png, output-1,jpg, output-2.jpg, etc.)

---

### Post by HermanAB on 2018-08-27
How to convert? You almost answered your own question:
$ convert -density 600 file.pdf file.jpg

---

