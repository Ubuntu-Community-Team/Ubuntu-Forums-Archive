---
title: "Imagescan PDF only"
date: 2017-07-28
forum: General Help
---

### Post by angel mike on 2017-07-28
I have just installed Imagescan bundle for ubuntu 16.04 from Epson site for use on Epson Flatbed Scanner Prefection V39.
It only seems to support PDF file output is this correct?
Thanks

---

### Post by angel mike on 2017-07-28
I think I have resolved this issue by using ImageMagick to convert to various formats.
i'll mark solved.

---

### Post by vocx on 2017-07-28
> **angel mike said:**
> I think I have resolved this issue by using ImageMagick to convert to various formats.
i'll mark solved.
ImageMagick to convert to various formats is fine, however, you should still find a way to produce a bitmap (.jpg, .png, .bmp, etc.) directly from the scanner.

You see, PDFs typically include images in compressed JPG. This means that if you convert a PDF to JPG using "convert", it will go through a second round of compression, which will probably result in a bad image, and sometimes an even larger output file size.

I don't have experience with your Epson scanner, but for my multifunctional HP printer-scanner, I just use the default program in Ubuntu, called "simple-scan".
```

sudo apt install simple-scan
simple-scan

```

I can scan and save the resulting file as ".pdf", ".png", and ".jpg". It's possible the output formats depend on the specific scanner. If you don't have there anything else than PDF, maybe it's a driver issue that you need to solve first.

---

