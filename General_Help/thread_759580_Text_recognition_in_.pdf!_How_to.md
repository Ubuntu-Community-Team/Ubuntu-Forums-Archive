---
title: "Text recognition in *.pdf! How to?"
date: 2008-04-19
forum: General Help
---

### Post by LasseNC on 2008-04-19
Hello guys! 

I am about to start a project that involves extracting alot of text that has been saved in *.pdf as images. 

Do you know any programs that can do OCR and let me extract the text for me? 

Kind regards, Lasse

---

### Post by marufaberlin on 2008-04-19
well first of all I'd try to extract the images as jpegs or something else. Any good PDF viewer will allow you to do that with good ol' copy 'n paste. Then run it through gocr.

---

### Post by LasseNC on 2008-04-19
Can you recommend a good *.pdf viewer? Only have the standard ubuntu one.

---

### Post by TeoBigusGeekus on 2008-04-19
Kpdf kicks ***!!!

---

### Post by trippinnik on 2008-04-19
doesn't tracker search the contents of pdfs?

---

### Post by LasseNC on 2008-04-19
Where do you find the OCR function in kpdf?

---

### Post by ryanhaigh on 2008-04-19
```

#!/bin/bash

#Script to convert a pdf containing images to a ppm images and then to 
#text using optical character recognition.

#need to change to allow spaces in filenames
#need to use text substitution to improve filenaming.

#convert all pdfs to ppm images
for pdf in `ls *.pdf`
do
    pdftoppm $pdf $pdf.ppm
done

#use gocr to convert ppm images to txt files
for ppm in `ls *.ppm`
do
    gocr $ppm > $ppm.txt
done
exit

```

---

### Post by LasseNC on 2008-04-19
Stop talking in space-ish! :P I didn't get anything there!

Not this part atleast:

#convert all pdfs to ppm images
for pdf in `ls *.pdf`
do
    pdftoppm $pdf $pdf.ppm
done

---

### Post by LasseNC on 2008-04-19
Wrote this in terminal:

pdftoppm /home/lasse/Documents/AJS/Projekt/2.pdf ppmpdf.ppm

Comes up with nothing, so I'm abit clueless from here.

Update:

Think I was a bit too quick there, after letting Terminal being open for a little time, it started making the pictures! 

Will report back!

---

### Post by LasseNC on 2008-04-19
They come up in ppm now, but I need to rotate them 90 degrees to the left, any idea of how to mass rotate all these files?

I have around 100 pdf files to do this with, any way of doing this in one go to all files?

---

### Post by LasseNC on 2008-04-19
```
all: ppm-copy ppm-rotate

clean:
	rm -f *.o ppm-copy ppm-rotate

.SUFFIXES: .cpp .o

.cpp.o: g++ -c $*.cpp 

ppm-prim.o: ppm-prim.h
ppm-copy.o: ppm-prim.h
ppm-rotate.o: ppm-prim.h

ppm-copy: ppm-copy.o ppm-prim.o
	g++ -o ppm-copy ppm-copy.o ppm-prim.o

ppm-rotate: ppm-rotate.o ppm-prim.o
	g++ -o ppm-d rotate ppm-rotate.o ppm-prim.o

```

Looks like it could be of use, but I don't fully understand the pre/suffixes

---

### Post by ryanhaigh on 2008-04-19
Ok modified the script to include a rotation 90 deg to the left.
```

#!/bin/bash

#Script to convert a pdf containing images to a ppm images and then to 
#text using optical character recognition.

#need to change to allow spaces in filenames
#need to use text substitution to improve filenaming.

#convert all pdfs to ppm images
for pdf in `ls *.pdf`               #for every file with pdf extension
do
    pdftoppm $pdf $pdf.ppm          #convert pdf to ppm image
done

#use gocr to convert ppm images to txt files
for ppm in `ls *.ppm`               #for every file with .ppm extension
do
    convert $ppm -rotate -90 $ppm   #rotates image 90deg left
    gocr $ppm > $ppm.txt            #converts image to text with OCR
done
exit

```

Save this into a text file and call it pdf2ppm2text.sh or whatever you want, right click on the file and change permissions to allow exectuting as a program. Place the file in the directory with all the pdfs in it. Open a terminal and change to the directory with all the pdfs in it. Then do the following

```

./pdf2ppm2text.sh

```

This script will take care of all the files in the directory as indicated by the comments. You could also remove the temporary ppm file if you wanted by adding another line after the gocr line ```
rm $ppm
```

---

### Post by ryanhaigh on 2008-06-23
geoffree I cannot recall having used kooka to do the optical character recognition, there was one gtk based tool that did a reasonable job but in the end they are just frontends to the commandline. The problem may be that the scanner is not able to output in a format that gocr can read. If you have a look at the man page for gocr only certain formats are available.
```
man gocr
```
The easiest thing to do would probably be to scan the image to a jpeg then use a command line tool to convert that to a pnm image which gocr recognises.
```
jpegtopnm scan.jpg scan.pnm
```
You can then use gocr from the command line to convert to text.
```
gocr scan.pnm > scanedtext.txt
```

---

### Post by geoffree on 2008-07-14
> **ryanhaigh said:**
> geoffree I cannot recall having used kooka to do the optical character recognition, there was one gtk based tool that did a reasonable job but in the end they are just frontends to the commandline. The problem may be that the scanner is not able to output in a format that gocr can read. If you have a look at the man page for gocr only certain formats are available.
```
man gocr
```
The easiest thing to do would probably be to scan the image to a jpeg then use a command line tool to convert that to a pnm image which gocr recognises.
```
jpegtopnm scan.jpg scan.pnm
```
You can then use gocr from the command line to convert to text.
```
gocr scan.pnm > scanedtext.txt
```
I realize its been a little while but I owe you a thanks for responding to my query.
Its valuable and valued when people respond to pleas from those with problems.

geoffrey

---

