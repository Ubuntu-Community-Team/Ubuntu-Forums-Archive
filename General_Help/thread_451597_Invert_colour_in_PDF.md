---
title: "Invert colour in PDF?"
date: 2007-05-22
forum: General Help
---

### Post by bogoliubov on 2007-05-22
Hello. I have created a presentation in Impress. It has a black background and white text/graphics, and I'm quite happy with the result.
Now to the problem: I'd like to print it since I'd like to make some notes on it etc. But it will waste an awful amount of toner since almost everything is black! So, can I invert the colours somehow? I only need to invert them for the printing, not for saving a in a different file.

I guess I can make PNGs or something out of each page, but that seems a bit tricky...
All ideas are greatly appreciated!

---

### Post by benmoreassynt on 2007-05-22
> **bogoliubov said:**
> Hello. I have created a presentation in Impress. It has a black background and white text/graphics, and I'm quite happy with the result.
Now to the problem: I'd like to print it since I'd like to make some notes on it etc. But it will waste an awful amount of toner since almost everything is black! So, can I invert the colours somehow? I only need to invert them for the printing, not for saving a in a different file.

I guess I can make PNGs or something out of each page, but that seems a bit tricky...
All ideas are greatly appreciated!

You could do this (there will be other ways):

Export impress file to pdf using OO gui.

use pdfimages at command line to export pdf to image files.
For example the following will convert all pdfs in a directory to pbm images (you can specify jpg as well):
```
pdfimages *.pdf
```

Then use image-magick's mogrify to invert the colours. This should convert all the pbms in a directory:

```
mogrify -negate *pbm
```

Image-magick should be installed by default. I cannot remember if pdfimages is, but you can install it through apt-get or aptitude,

I'm sure there is a way to easily import them back into a pdf, although it escapes me right now.

---

### Post by bogoliubov on 2007-05-22
Ok, I'll try this if I can't find anything else. I was hoping for a way of doing it with the PDF, but I guess this works just for printing...

Thanks!

---

### Post by benmoreassynt on 2007-05-22
Actually, try:

mogrify -negate *.pdf

It may well be able to handle pdfs without exporting them.

---

### Post by bogoliubov on 2007-05-23
Thanks, that worked; although with bad resolution. But since I only needed it for making notes on, it's ok. Thanks!

---

