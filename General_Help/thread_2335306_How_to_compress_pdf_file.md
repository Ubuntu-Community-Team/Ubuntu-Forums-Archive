---
title: "How to compress pdf file"
date: 2016-08-27
forum: General Help
---

### Post by satimis on 2016-08-27
Hi all,

Is there an easy way to compress pdf file?  I don't have pdf-compressor installed.

Existing pdf size - 9.5MB 
I need to compress it to about 3MB

I used the online pdf compressor
[http://www.ilovepdf.com/compress_pdf](http://www.ilovepdf.com/compress_pdf)

compressing it to 4.6MB.  But I couldn't compress it again, the second time.

I have "convert" here.

Please help.  Thanks

Regards
satimis

---

### Post by Impavidus on 2016-08-27
What makes you think that pdf file can be compressed more?

There are several tricks to compress pdf. Stripping unused characters from fonts, stripping hidden information, increasing the compression level of embedded raster images, reducing the resolution of those images, even replacing rasterised text with ordinary text using OCR is a form of pdf compression. If your pdf compression tool used all tricks it could use without severely reducing quality, more compression is not possible in a second run of the tool.

You could try and reduce the quality of embedded raster images (if any, but in such a large pdf there usually are) and rebuild the pdf, if you made it yourself.

---

### Post by satimis on 2016-08-27
> **Impavidus said:**
> What makes you think that pdf file can be compressed more?

There are several tricks to compress pdf. Stripping unused characters from fonts, stripping hidden information, increasing the compression level of embedded raster images, reducing the resolution of those images, even replacing rasterised text with ordinary text using OCR is a form of pdf compression. If your pdf compression tool used all tricks it could use without severely reducing quality, more compression is not possible in a second run of the tool.

You could try and reduce the quality of embedded raster images (if any, but in such a large pdf there usually are) and rebuild the pdf, if you made it yourself.
Hi,

Thanks for your advice

The pdf is a scanned "Fill-in Form" completed with signature.  The file consists several pages.  I can't rebuild it.  Ah maybe I can split it into several files.

satimis

---

### Post by SeijiSensei on 2016-08-28
Does bzip2 help at all?  I reduced a PDF from 10M to 3M just now.  Even plain old zip reduced it to 4M.

---

### Post by sudodus on 2016-08-28
I have a script ***rpdf***, that uses ***gs*** (GhostScript) and can compress pdf files. I have not used it much recently, but I tested it now in 16.04 LTS with a pdf manual and 'screen quality'. It compressed from 11 MiB to 4.1 MiB. ***bzip2*** is efficient on the original file, but cannot do much with the file, that is already shrunk with the script rpdf.

```
 11M nov 18  2010 Panasonic_HDC-TM700_manual.pdf
5,7M aug 28 19:39 Panasonic_HDC-TM700_manual.pdf.bz2
4,1M aug 28 19:39 Panasonic_HDC-TM700_manual_screen.pdf
3,9M aug 28 19:40 Panasonic_HDC-TM700_manual_screen.pdf.bz2
```

Another pdf file was compressed from 4.8 MiB to 2.2 MiB. The ratio depends very much on the content of the pdf file.

```
#! /bin/bash

if [ "$1" == "" ]
then
 echo "Usage $0 <pdf-file> [1|2|3|4]"
 echo "ex.   $0 name.pdf 1 --> screen quality"
 echo "ex.   $0 name.pdf 2 --> ebook quality"
 echo "ex.   $0 name.pdf 3 --> printer quality"
 echo "ex.   $0 name.pdf 4 --> prepress quality"
 echo "Quit from the GS> prompt with 'quit' (and the Enter key)"
 exit
fi

if [ "$2" == "" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4  \
    -sOutputFile="${1/%.pdf}_r.pdf" "$1"
elif [ "$2" == "1" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
    -dPDFSETTINGS=/screen -sOutputFile="${1/%.pdf}_screen.pdf" "$1"
elif [ "$2" == "2" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
    -dPDFSETTINGS=/ebook -sOutputFile="${1/%.pdf}_ebook.pdf" "$1"
elif [ "$2" == "3" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
    -dPDFSETTINGS=/printer -sOutputFile="${1/%.pdf}_printer.pdf" "$1"
elif [ "$2" == "4" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
    -dPDFSETTINGS=/prepress -sOutputFile="${1/%.pdf}_prepress.pdf" "$1"
else
 echo "No such alternative: $2"
fi


```

---

### Post by aerodinesh on 2016-10-25
> **sudodus said:**
> I have a script ***rpdf***, that uses ***gs*** (GhostScript) and can compress pdf files. I have not used it much recently, but I tested it now in 16.04 LTS with a pdf manual and 'screen quality'. It compressed from 11 MiB to 4.1 MiB. ***bzip2*** is efficient on the original file, but cannot do much with the file, that is already shrunk with the script rpdf.

```
 11M nov 18  2010 Panasonic_HDC-TM700_manual.pdf
5,7M aug 28 19:39 Panasonic_HDC-TM700_manual.pdf.bz2
4,1M aug 28 19:39 Panasonic_HDC-TM700_manual_screen.pdf
3,9M aug 28 19:40 Panasonic_HDC-TM700_manual_screen.pdf.bz2
```

Another pdf file was compressed from 4.8 MiB to 2.2 MiB. The ratio depends very much on the content of the pdf file.

```
#! /bin/bash

if [ "$1" == "" ]
then
 echo "Usage $0 <pdf-file> [1|2|3|4]"
 echo "ex.   $0 name.pdf 1 --> screen quality"
 echo "ex.   $0 name.pdf 2 --> ebook quality"
 echo "ex.   $0 name.pdf 3 --> printer quality"
 echo "ex.   $0 name.pdf 4 --> prepress quality"
 echo "Quit from the GS> prompt with 'quit' (and the Enter key)"
 exit
fi

if [ "$2" == "" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4  \
    -sOutputFile="${1/%.pdf}_r.pdf" "$1"
elif [ "$2" == "1" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
    -dPDFSETTINGS=/screen -sOutputFile="${1/%.pdf}_screen.pdf" "$1"
elif [ "$2" == "2" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
    -dPDFSETTINGS=/ebook -sOutputFile="${1/%.pdf}_ebook.pdf" "$1"
elif [ "$2" == "3" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
    -dPDFSETTINGS=/printer -sOutputFile="${1/%.pdf}_printer.pdf" "$1"
elif [ "$2" == "4" ]
then
 gs -dNOPAUSE -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 \
    -dPDFSETTINGS=/prepress -sOutputFile="${1/%.pdf}_prepress.pdf" "$1"
else
 echo "No such alternative: $2"
fi


```

Hi Friend,
How to use ur script? Little guide or syntax will help me. Thanks in advance.

---

### Post by T2uiYKb7 on 2016-10-25
You can open the PDF with an archive viewer (right click on the file) then compress the image files with Gimp and put them back in if you want.

---

### Post by howefield on 2016-10-25
> **aerodinesh said:**
> How to use ur script? Little guide or syntax will help me. Thanks in advance.

Try copying/pasting the script into a text editor and save it, say as rpdf, then right click the saved text file and select Properties > Permissions tab and check off "*Allow executing file as program*". Then use

```
./rpdf path_and_name_of_pdf_to_be_processed
```

You should use the path to the rpdf file if you are not already in the same folder.

---

### Post by sudodus on 2016-10-25
> **aerodinesh said:**
> Hi Friend,
How to use ur script? Little guide or syntax will help me. Thanks in advance.

- Create the directory **~/bin** with the following commands in a terminal window

```
cd
mkdir bin
```

- Copy and paste the content of the script from my previous post into a text editor.

- Save it with a suitable name (in the directory ~/bin), for example **rpdf**, (~/bin/rpdf).

- Make the file executable

```
cd
cd bin
chmod ugo+x rpdf
```

- Reboot the computer to make it recognize that it should search for executable files in your bin directory.

- Now, run the following command (blue) and you should get the following help text (black)

```
$ **[COLOR="#0000FF"]rpdf[/COLOR]**
Usage /home/sudodus/bin/rpdf <pdf-file> [1|2|3|4]
ex.   /home/sududus/bin/rpdf name.pdf 1 --> screen quality
ex.   /home/sudodus/bin/rpdf name.pdf 2 --> ebook quality
ex.   /home/sudodus/bin/rpdf name.pdf 3 --> printer quality
ex.   /home/sudodus/bin/rpdf name.pdf 4 --> prepress quality
Quit from the GS> prompt with 'quit' (and the Enter key)
```

- So if you have the file **bigfile.pdf**, you can try the following command line (with rpdf in your bin directory, you need not use the full path to rpdf). If you change directory to where you keep your pdf files, you need no path to the pdf file, only the file name, but if your current directory is another one, you need the full path to the pdf file as described by *howefield*.

```
$ [COLOR="#0000FF"]rpdf bigfile.pdf 1[/COLOR]
GPL Ghostscript 9.18 (2015-10-05)
Copyright (C) 2015 Artifex Software, Inc.  All rights reserved.
This software comes with NO WARRANTY: see the file PUBLIC for details.
Processing pages 1 through 31.
Page 1
Page 2
Page 3
Page 4
Page 5
Page 6
Page 7
Page 8
Page 9
Page 10
Page 11
Page 12
Page 13
Page 14
Page 15
Page 16
Page 17
Page 18
Page 19
Page 20
Page 21
Page 22
Page 23
Page 24
Page 25
Page 26
Page 27
Page 28
Page 29
Page 30
Page 31
GS>[COLOR="#0000FF"]quit[/COLOR]
$ [COLOR="#0000FF"]ls -lh bigfile*[/COLOR]
-rw-rw-r-- 1 sudodus sudodus [COLOR="#FF0000"]1.9M[/COLOR] okt 25 09:38 bigfile.pdf
-rw-rw-r-- 1 sudodus sudodus [COLOR="#FF0000"]1.3M[/COLOR] okt 25 09:44 bigfile_screen.pdf
$ 
```

- Scroll the code window to see the result. In this case the size was reduced from 1.9 MiB to 1.3 MiB.

---

