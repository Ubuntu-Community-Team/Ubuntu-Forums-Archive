---
title: "I can do it 1 page at a time but I want to convert all pdf page to jpgs Help, please!"
date: 2008-04-04
forum: General Help
---

### Post by s3a on 2008-04-04
I have pdf's with multiple pages, is there any way I can use gimp or another program to convert pdfs with multiple pages to multiple jpegs.

Thanks in advance!

---

### Post by ibuclaw on 2008-04-04
You can use the terminal.

Imagemagick provides a command called **convert** that can convert anything into anything (That's an image document).

```
 convert sample.pdf sample.jpeg 
```

I've just tried it on a one page document.
It works fine...
Gives off a few warnings, namely:
[QUOTE=my terminal output]
   **** Warning: Fonts with Subtype = /TrueType should be embedded.
                 The following fonts were not embedded:
			Arial
			Arial,Bold
			Arial,Italic
			TimesNewRoman

   **** This file had errors that were repaired or ignored.
   **** The file was produced by: 
   **** >>>> Acrobat PDFWriter 4.05 for Windows NT <<<<
   **** Please notify the author of the software that produced this
   **** file that it does not conform to Adobe's published PDF
   **** specification.
[/QUOTE]
 but not to worry, I compared the two and they both seem perfectly equal!

I'll get back to you in a minute once I test multiple page documents.

Regards
Iain

---

### Post by ibuclaw on 2008-04-04
Yes. It works!
No Problems.


Though I would give it a separate folder to store all the files in if I were you.

```

mkdir sample
convert sample.pdf sample/sample.jpeg 
```
Depending how many pages you have, it may take up to a minute (30 seconds it took me to do 100 pages or a pdf file sized 500KB.).

If you have multiple pdfs that you want to convert, a simple script would be:
```

#!/bin/bash
for i in *.pdf; do
    export j=$(echo "$i" | sed -e "s/.pdf//")
    mkdir -p "$j"
    echo "converting "$i" into "$j".jpeg"
    convert "$i" "$j"/"$j".jpeg
done

```
Put all the pdfs into one folder, including the script, mark the script executable (**chmod +x pdf2jpeg.sh** for example), then all shall be converted into separate jpegs and put in their own named folder.

Regards
Iain

---

### Post by ibuclaw on 2008-04-04
I've just had a real life try at the script.

And all is well.

Though if you are converting, say a dozen books with 500 pages each, expect nothing to happen for about 5 minutes, then expect your PC to be rather CPU intensive, rather quickly.

I suggest leaving your box to run it's batch first. And come back later.

As I said, it does vary due to the size of the script.
A 500 page pdf I just tried took 10 minutes.

Another note to point out is that due to the size of the jpegs.
A 10MB pdf file can inflate to 100MBs worth of Jpegs.

So perhaps compressing the image a bit may help
```
 find $(pwd) -name "*.jpeg" -execdir mogrify -quality 75 "{}" \;
```
That knocked it down to 70MBs while still allowing acceptable reading quality.

Though 80 may be a safe number. 90 may inflate your folder even more.


[EDIT]
Png's have a better quality and compression rate than Jpegs.
I recommend that you try converting them to that format instead.

Regards
Iain

---

### Post by chadoh on 2008-07-08
> **tinivole said:**
> 
```

mkdir sample
convert sample.pdf sample/sample.jpeg 
```

```

#!/bin/bash
for i in *.pdf; do
    export j=$(echo "$i" | sed -e "s/.pdf//")
    mkdir -p "$j"
    echo "converting "$i" into "$j".jpeg"
    convert "$i" "$j"/"$j".jpeg
done

```
Put all the pdfs into one folder, including the script, mark the script executable (**chmod +x pdf2jpeg.sh** for example), then all shall be converted into separate jpegs and put in their own named folder.

Regards
Iain

Wow! I've wanted a program that does this and here ubuntu had the tool to do it the whole time! Thank you so much!

I think this function should be made more obvious. When an image that can be converted is right-clicked, a "convert" option should be in the menu.

What all does this work with? Images, clearly. Audio files? Movies? Text? Spreadsheets & presentations?

Thank you!

---

### Post by kaibob on 2008-07-08
The mogrify command from the Imagemagick suite will also do this. Just copy all of the PDF files to an empty directory, open a terminal window, change to the target directory, and enter:

```
mogrify -format jpg *.pdf
```

Mogrify retains the base file name and adds a number when the PDF contains more than one page. Thus, if test.pdf contains 1 page, mogrify creates test.jpg, and if test.pdf contains 2 pages, mogrify creates test-1.jpg and test-2.jpg.

A listing of the formats that mogrify and convert will work with can be found at:

[http://www.imagemagick.org/script/formats.php](http://www.imagemagick.org/script/formats.php)

---

