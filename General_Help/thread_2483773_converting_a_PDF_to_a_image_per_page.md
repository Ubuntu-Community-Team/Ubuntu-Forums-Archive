---
title: "converting a PDF to a image per page"
date: 2023-02-08
forum: General Help
---

### Post by Skaperen on 2023-02-08
i have several PDF files that are mad of just images that i want to convert to image files (such as GIF or PNG).  searching Google only reviews websites that offer to do this online (maybe so they can collect a copy of every PDF document in the world).  i want to get actual free open source software that does this, which builds (as needed) an runs on Ubuntu, or know the name of it if it already is available in the Ubuntu repository.  i will be building an automated system and the documents can contain confidential info.  i will also be processing these images via tesseract OCR and building a search index.

so, what should i look for or install?

---

### Post by monkeybrain20122 on 2023-02-08
You need to install imagemagick (if it is not installed already)

then, for example, if you want to convert to png
```

covert input.pdf output.png
```

But not so fast, if you do just that you will get an error message because the function is blocked for security reasons. The security vulnerability was addressed in gs 9.24 You want to make sure it is safe to unblock it

so check your gs version, if >= 9.24, proceed to the next step (in my Ubuntu 22.04 gs --version returns 9.55.0)

Edit the file  /etc/ImageMagick-6/policy.xml with your favorite editor, e.g
```

sudo nano /etc/ImageMagick-6/policy.xml


```

Find the block 
```
<!-- disable ghostscript format types -->
<policy domain="coder" rights="none" pattern="PS" />
<policy domain="coder" rights="none" pattern="PS2" />
<policy domain="coder" rights="none" pattern="PS3" />
<policy domain="coder" rights="none" pattern="EPS" />
<policy domain="coder" rights="none" pattern="PDF" />
<policy domain="coder" rights="none" pattern="XPS" />



```

enclose the line with pattern="PDF" with <!-- and --> to comment it out, save. (there are two dashes, though it is hard to see here)

Then now you can run the convert command.

[https://stackoverflow.com/questions/52998331/imagemagick-security-policy-pdf-blocking-conversion/53180170#53180170](https://stackoverflow.com/questions/52998331/imagemagick-security-policy-pdf-blocking-conversion/53180170#53180170)


some people recommend pdftoppm [https://ubunlog.com/en/pdftoppm-convierte-archivos-pdf-en-imagenes/](https://ubunlog.com/en/pdftoppm-convierte-archivos-pdf-en-imagenes/)

[B]
Edited:[/B] You'd better create a folder and put your pdf and run convert in there because depending on the size of your pdf it may generate a lot of png files. You want to collect them in one place instead of spewing them all over your $HOME.

---

### Post by Holger_Gehrke on 2023-02-08
Another option would be pdfimages from the package poppler-utils. This will pull the images from a pdf as they are stored inside it without rendering pages.

Holger

---

### Post by ajgreeny on 2023-02-08
If you use convert as shown by monkeybrain you may need to set quality values in the command you use or you'll create a poor image.

I can't remember exactly what I have used in the past but will find it and tell you tomorrow when I manage to find my "aide-memoire" text file which isn't on this machine.

---

### Post by Skaperen on 2023-02-09
> **Holger_Gehrke said:**
> Another option would be pdfimages from the package poppler-utils. This will pull the images from a pdf as they are stored inside it without rendering pages.

Holger

i already have this package.  it sounds like the accurate way to get good images that should get better results from tesseract.

my gs version is 9.50 according to the ghostscript package so i can still try that if needed.

i assume that's a missing "n" in "covert".

---

