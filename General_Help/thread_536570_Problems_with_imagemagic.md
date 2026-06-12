---
title: "Problems with imagemagic"
date: 2007-08-27
forum: General Help
---

### Post by tzulberti on 2007-08-27
Hi. I am trying to convert a folder that contains almost 370 images to a pdf, with the following command:
convert *.jpg toerica.pdf

Nevertheless, the cpu get at 100%, and after a few minutes the followin output appears:
"Killed"...

and the pdf file was not created. Those someone knows the solution?

Also, is there a way to put more than one image per page in the pdf file?

I have tried to move some images (like 20) to another folder and then try to make a pdf file and that worked...

Thanks,
Tomas Zulberti

---

### Post by fenian on 2007-08-27
You can use OpenOffice Word Processor to create a PDF.This will allow you to put multiple images on a page add text etc...It's a little more work than having imagemagiik automatically
convert the files but I think you'll get a more satisfying result.

---

### Post by tzulberti on 2007-08-28
There are more than 350 images...
If there is no other solution, y would use openoffice. Thanks for the adivce.

---

### Post by vanadium on 2007-08-28
Indeed, imagemagicks is the way to go. It is important that you carefully read the command line syntax of any command line program you intend to use. The wildcard approach will not work here. Instead issue

```

for f in *.jpg; do convert $f $f.pdf; done

```

There are probably a few ways you can have multiple pictures in one PDF. One involves the use solely of the imagemagickx tools. You can combine several jpgs into one file, resize that file then do the conversion. Another approach would be to use tools that can composite several PDFs on one page. The multivalent tools ([http://multivalent.sourceforge.net/](http://multivalent.sourceforge.net/)) can do that.

---

