---
title: "Good program to compile several JPGs into a PDF?"
date: 2006-12-04
forum: General Help
---

### Post by magomago on 2006-12-04
I have like 30 JPGS I want to split into a few PDFs to make managing them easier (So I can have 3 files instead of 3 JPGs...or even 1 File and insert separators on my own)

I know I could technically import the images to OO writer and then save as PDF...but I would prefer another way that doesn't involve making a document out of the files first.

Is there a program out there that simply converts a collection of JPG files into one pdf?

Thanks :)

---

### Post by lamego on 2006-12-04
1) Install the package imagemagick
2) Open a terminal and run:
```
convert *jpg allinone.pdf
```
I didn't tried it myself, just found it with google ;)

---

### Post by Greguti on 2006-12-04
Hi

Give a chance to imagemagick, it's all piloted via the command line, but it's really powerful, with a lot of commands. The one you could use is ```
convert
``` : put all the jpg files you want to add to one pdf file in a specific folder. Then, open a terminal inside this folder, and run the following command:

```
convert *.jpg mycollection.pdf
```

You'll get all your jpg images inside a new pdf file (called mycollection.pdf in this example).

If you don't have the command convert, just install imagemagick in a terminal: ```
sudo apt-get install imagemagick
```

More informations here: [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

---

