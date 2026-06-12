---
title: "PDF to jpeg"
date: 2005-08-28
forum: General Help
---

### Post by dsbeav on 2005-08-28
Does anyone know of a good program or script to convert PDF files to jpeg, or of a plugin to convert Openoffice documents to jpegs?

Thanks!

---

### Post by matthew on 2005-08-28
Gimp. Open the file. Select your desired options from those given you. Then File->Save As. In the dialog box choose "save image as filetype" or something to that effect. Very easy.

---

### Post by dsbeav on 2005-08-28
[QUOTE=matthew]Gimp. Open the file. Select your desired options from those given you. Then File->Save As. In the dialog box choose "save image as filetype" or something to that effect. Very easy.[/QUOTE]


Do I need a pdf extension for GIMP?  It gives me an error when I try to open a pdf in GIMP. 

ERROR:

Opening '/home/dsbeav/genchem.pdf' failed:
Plug-In could not open image

---

### Post by buldir on 2005-08-28
You could try [gsview](http://www.cs.wisc.edu/~ghost/gsview/get47.htm).  Just download the .rpm and convert it to .deb format using alien:

```
sudo alien gsview-4.7-1.i386.rpm
sudo dpkg -i gsview*.deb
```

It converts postscript as well.

---

### Post by matthew on 2005-08-28
> Do I need a pdf extension for GIMP? It gives me an error when I try to open a pdf in GIMP.  
Hmm... I just tried it with mine and had no trouble opening a pdf. I looked at my plugins and didn't see anything specially for pdfs and I don't recall adding anything. I did just notice a rather unfortunate thing, though, with this method: it only opened the first page if you are opening a multi-page pdf file. So...maybe the other poster's method will work better.

---

### Post by JELaVallee on 2005-09-10
[QUOTE=buldir]You could try [gsview](http://www.cs.wisc.edu/~ghost/gsview/get47.htm).  Just download the .rpm and convert it to .deb format using alien:

```
sudo alien gsview-4.7-1.i386.rpm
sudo dpkg -i gsview*.deb
```

It converts postscript as well.[/QUOTE]

I've tried installing GSView using this method.  The installation appears to go well and I can start the application, but when I try to open any file, I get an error popup dialog with the message "Failed to load libgs.so: libgs.so: cannot open shared object file: No such file or directory"

I do have gs-gpl installed and its dependencies.

Zip results on find /|grep "libgs.so"

What am I missing?

Thanks!,
Etienne

---

### Post by buldir on 2005-09-10
OK, I ran into the same problem...stupid dependencies.  So, I would uninstall gsview:

```
sudo dpkg -r gsview
``` 

and install imagemagick if you haven't got it installed already:

```
sudo apt-get install imagemagick
```

The "convert" command is very powerful.  In the command line, type:

```
convert -quality 100 -density 300 my_doc.pdf my_doc.jpg
``` 

which will give you a very high quality jpg at 300 DPI.  [Here](http://www.imagemagick.org/script/convert.php#usage) is the information on "convert" from the ImageMagick web site.  Hope this helps.

---

