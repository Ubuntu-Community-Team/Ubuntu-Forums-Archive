---
title: "join two pdf files"
date: 2007-10-08
forum: General Help
---

### Post by sumanta on 2007-10-08
How to join two pdf files.

---

### Post by anaconda on 2007-10-08
imagemagick:s convert is really handy tool
You might have to install it first:
```
sudo apt-get install imagemagick
```

```
convert file1.pdf file2.pdf file3.pdf out.pdf
```

FYI: one other thing I sometimes need is
```
convert *.jpg out.pdf
```
makes a pdf out of photos (of a book or something..)

---

### Post by vanadium on 2007-10-08
I am not sure whether this is the way to go. When I combined a 1GB and a 4 GB pdf, a 64GB PDF resulted. This is because the PDF's are not combined as such, but converted to bitmap graphics then embedded in a PDF. pdftk, which you can find in the repositories, will allow you to combine PDF's easily. You can also do it with gs, which certainly is already installed on your system, but the command line syntax is a bit awkward.

Good tip, though, on how to combine jpg's into one PDF. However, also here, we will probably have an inflation of bytes (the size of the PDF being much larger than the sum of the jpgs).

---

### Post by mali2297 on 2007-10-08
As already mentioned, Pdftk will do this easily. Install it and run from the terminal:
```

pdftk file1.pdf file2.pdf cat output file12.pdf

```
Here *file1.pdf* and *file2.pdf* are merged into *file12.pdf*.

---

### Post by vanadium on 2007-10-08
By the way, merging jpg's into a PDF works very nicely!

---

