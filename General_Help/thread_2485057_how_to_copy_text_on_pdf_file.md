---
title: "how to copy text on pdf file"
date: 2023-03-18
forum: General Help
---

### Post by satimis on 2023-03-18
Hi all,

It is quite strange to me.  Some pdf files I can select and copy text but some pdf files I can't select and copy text.

Is there a solution?  Thanks

Regards

---

### Post by Holger_Gehrke on 2023-03-18
Does the cursor change to the text cursor (vertical I-beam) when it's on top of the text in the PDF-files from which you can't copy text ? If it doesn't, then the 'text' is no text but a pixel image of text. You can read it, but your computer can't tell that this is text.

Alternatively it might be that the author of the PDF has set a permissions password and disallowed copy and paste and your reader is honouring the authors wishes.

Holger

---

### Post by satimis on 2023-03-18
> **Holger_Gehrke said:**
> Does the cursor change to the text cursor (vertical I-beam) when it's on top of the text in the PDF-files from which you can't copy text ? If it doesn't, then the 'text' is no text but a pixel image of text. You can read it, but your computer can't tell that this is text.

Alternatively it might be that the author of the PDF has set a permissions password and disallowed copy and paste and your reader is honouring the authors wishes.

Holger
Hi,

Thanks for your advice.  There is no change moving the cursor over the text which I expect to copy.  Can I import file to GIMP to copy the text?

Regards

---

### Post by Holger_Gehrke on 2023-03-18
Yes, GIMP can import PDF and will allow you to select part of the image to copy and paste it. That still doesn't turn that image to text. You can't search for it, it won't re-flow or do any of the other things you'd expect to be able to do to text. If it's just a short bit of text (a few sentences, a paragraph at most), I'd just retype it. For longer parts I'd pull it apart using pdfimages from the poppler tools and feed the pages to tesseract or one of the other OCR tools (**O**ptical **C**haracter **R**ecognition, a program that 'reads' images and turns them into text). OCR might seem like a great idea, but usually it's highly dependent on image quality and complexity of the layout of the text. Turning a short User's Manual - about 12 pages, each slightly smaller than A5 - that came in a pdf made up of images into something usable by running it through OCR and using LibreOffice to correct the mistakes made by the OCR and lay it out again in a way similar to the original took me 4-5 hours the last time I did that. Admittedly there were several tables in that manual and some images which were promptly turned into letter salad by tesseract, but it still was less work than retyping the whole thing.

Holger

---

### Post by satimis on 2023-03-18
> **Holger_Gehrke said:**
> Yes, GIMP can import PDF and will allow you to select part of the image to copy and paste it. That still doesn't turn that image to text. You can't search for it, it won't re-flow or do any of the other things you'd expect to be able to do to text. If it's just a short bit of text (a few sentences, a paragraph at most), I'd just retype it. For longer parts I'd pull it apart using pdfimages from the poppler tools and feed the pages to tesseract or one of the other OCR tools (**O**ptical **C**haracter **R**ecognition, a program that 'reads' images and turns them into text). OCR might seem like a great idea, but usually it's highly dependent on image quality and complexity of the layout of the text. Turning a short User's Manual - about 12 pages, each slightly smaller than A5 - that came in a pdf made up of images into something usable by running it through OCR and using LibreOffice to correct the mistakes made by the OCR and lay it out again in a way similar to the original took me 4-5 hours the last time I did that. Admittedly there were several tables in that manual and some images which were promptly turned into letter salad by tesseract, but it still was less work than retyping the whole thing.

Holger
Agreed.  For short text, I would just retype it.

There are several methods available:-

1)
IMAGE TO TEXT CONVERTER - OCR ONLINE
[https://www.onlineocr.net/](https://www.onlineocr.net/)

2)
How To Convert Images To Text On The Linux Command Line With OCR
[https://www.howtogeek.com/devops/how-to-convert-images-to-text-on-the-linux-command-line-with-ocr/](https://www.howtogeek.com/devops/how-to-convert-images-to-text-on-the-linux-command-line-with-ocr/)

3)
Install PDF2OCR - Convert Images/Pdf into Text on Ubuntu
PDF2OCR - Convert Images/Pdf into Text
[https://snapcraft.io/install/pdf2go/ubuntu](https://snapcraft.io/install/pdf2go/ubuntu)

I'll try 3) above.  What will be your suggestion?  Thanks

Regards

---

### Post by ne29914 on 2023-03-18
I'd just use the online OCR converter. There are several and it's easier than installing one yourself.

---

### Post by Holger_Gehrke on 2023-03-18
1) I avoid online services if at all possible. If there's anything personal or confidential in that pdf then so should you.
2) is basically what I already do, but the tutorial uses pdftoppm - which renders the pages into various image files - while I use pdfimages - which pulls the images out of the pdf. This means I get the images as they are while anyone following that tutorial  gets images scaled to 150 ppi. Yes, pdftoppm has options to change that scaling; no the tutorial doesn't mention them; and why scale at all ?
3) pdf2ocr is new to me. While the software app says it's open source, the home page linked in the description does not link to any source code and neither the entry in Software nor the one on snapcraft nor the description on the homepage gives any details  about the program beyond two screenshots ... If I wanted a GUI for my OCR I'd probably use gImageReader (it's in the repositories, and the homepage given in the description is the github repository with the source ...)

Holger

---

### Post by satimis on 2023-03-18
> **Holger_Gehrke said:**
> 1) I avoid online services if at all possible. If there's anything personal or confidential in that pdf then so should you.
2) is basically what I already do, but the tutorial uses pdftoppm - which renders the pages into various image files - while I use pdfimages - which pulls the images out of the pdf. This means I get the images as they are while anyone following that tutorial  gets images scaled to 150 ppi. Yes, pdftoppm has options to change that scaling; no the tutorial doesn't mention them; and why scale at all ?
3) pdf2ocr is new to me. While the software app says it's open source, the home page linked in the description does not link to any source code and neither the entry in Software nor the one on snapcraft nor the description on the homepage gives any details  about the program beyond two screenshots ... If I wanted a GUI for my OCR I'd probably use gImageReader (it's in the repositories, and the homepage given in the description is the github repository with the source ...)

Holger

gImageReader ???
[https://flathub.org/apps/details/io.github.manisandro.gImageReader](https://flathub.org/apps/details/io.github.manisandro.gImageReader)

I'll try installing it on Ubuntu 22.04 VM.  Also I'll try pdf2ocr on another Ubuntu 22.04 VM

Regards

---

### Post by MAFoElffen on 2023-03-18
LOL... Installing new stuff that I'll probably only use once... I also usually spin up a VM to do what I need to do, then get rid of that VM when done. That way it keeps my main system clean from any fluff (usually other dependencies) that also get installed.

---

### Post by satimis on 2023-03-19
> **MAFoElffen said:**
> LOL... Installing new stuff that I'll probably only use once... I also usually spin up a VM to do what I need to do, then get rid of that VM when done. That way it keeps my main system clean from any fluff (usually other dependencies) that also get installed.
Hi,

This is my usual practice, testing software new to me on VM.  In case of problem I just delete the VM or if I don't need it after testing.  If I need it I'll install it on the Host after successful testing.

Regards

---

### Post by satimis on 2023-03-23
> **Holger_Gehrke said:**
> 1) - snip -
If I wanted a GUI for my OCR I'd probably use gImageReader (it's in the repositories, and the homepage given in the description is the github repository with the source ...)

Hi Holger,

Now I have gImageReader installed and running on Ubuntu 22.04.

Please advice can I use it on other languages, such as Chinese?  Thanks

Regards

---

### Post by Holger_Gehrke on 2023-03-23
There are language files for tesseract available in the repositories. If the files for a language are installed, gimagereader will offer that language in the dropdown menu visible in your screenshot.
```

apt search tesseract-ocr-

```
will show you the available languages and
```

sudo apt install tesseract-ocr-chi-sim tesseract-chi-sim-vert tesseract-chi-tra tesseract-chi-tra-vert

```
would install simplified Chinese, simplified Chinese vertical, traditional Chinese, and traditional Chinese vertical.

Holger

---

### Post by satimis on 2023-03-23
> **Holger_Gehrke said:**
> There are language files for tesseract available in the repositories. If the files for a language are installed, gimagereader will offer that language in the dropdown menu visible in your screenshot.
```

apt search tesseract-ocr-

```
will show you the available languages and
```

sudo apt install tesseract-ocr-chi-sim tesseract-chi-sim-vert tesseract-chi-tra tesseract-chi-tra-vert

```
would install simplified Chinese, simplified Chinese vertical, traditional Chinese, and traditional Chinese vertical.

Holger
Thanks for your advice.  Performed following steps

$ sudo apt update

$ sudo apt install tesseract-ocr-chi-sim tesseract-chi-sim-vert tesseract-chi-tra tesseract-chi-tra-vert```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package tesseract-chi-tra is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package tesseract-chi-sim-vert
E: Package 'tesseract-chi-tra' has no installation candidate
E: Unable to locate package tesseract-chi-tra-vert

```

$ apt policy tesseract-chi-sim tesseract-chi-tra tesseract-chi-tra-vert
tesseract-chi-sim:```

  Installed: (none)
  Candidate: (none)
  Version table:
tesseract-chi-tra:
  Installed: (none)
  Candidate: (none)
  Version table:
N: Unable to locate package tesseract-chi-tra-vert

```

The packages are not there.

Regards

---

### Post by Holger_Gehrke on 2023-03-23
Sorry, typo, missing 'ocr-' between 'tesseract-' and 'chi-' on three of the four package names. 

So the package names should be 'tesseract-ocr-chi-tra', 'tesseract-ocr-chi-tra-vert',  'tesseract-ocr-chi-sim' and 'tesseract-ocr-chi- sim-vert'.

Holger

---

### Post by satimis on 2023-03-23
> **Holger_Gehrke said:**
> Sorry, typo, missing 'ocr-' between 'tesseract-' and 'chi-' on three of the four package names. 

So the package names should be 'tesseract-ocr-chi-tra', 'tesseract-ocr-chi-tra-vert',  'tesseract-ocr-chi-sim' and 'tesseract-ocr-chi- sim-vert'.

Holger
Thanks for your advice.
```

sudo apt install tesseract-ocr-chi-sim tesseract-orc-chi-sim-vert tesseract-ocr-chi-tra tesseract-orc-chi-tra-vert

```
It went through without complaint.

Still I couldn't select and copy text.  Spell dictionary missing.  How can I install it?  Thanks
(pls refer to screenshot)

Regards

---

### Post by ActionParsnip on 2023-03-23
Lots of online PDF to ODT converters
[https://www.zamzar.com/convert/pdf-to-odt/](https://www.zamzar.com/convert/pdf-to-odt/)

---

### Post by satimis on 2023-03-23
> **ActionParsnip said:**
> Lots of online PDF to ODT converters
[https://www.zamzar.com/convert/pdf-to-odt/](https://www.zamzar.com/convert/pdf-to-odt/)
Hi,

Thanks for your advice and link

I can convert .pdf file to .odt online and open it on Libre Office Write.  But still they are images.  I couldn't copy its text.

Regards

---

### Post by Holger_Gehrke on 2023-03-23
> **satimis said:**
> 
Still I couldn't select and copy text.  Spell dictionary missing.  How can I install it?  Thanks
(pls refer to screenshot)


That's strange. A spelling dictionary for a writing system that uses ideograms ? Makes very little sense ... I tried it myself and got the same message; hit the 'close' button on the error message and marked part of my image for recognition, hit the recognize button, and recognition proceeded, producing a text panel full of symbols I wouldn't know how to enter (or read ...), not all - but most - of them identical to the ones in the image. What's especially strange about this is that I don't get an error like that when recognizing Japanese, which also uses ideograms (but also two syllabaries, so for words written using hiragana and katakana a spelling dictionary to enhance recognition would make some limited sense ...). Looks like a minor bug to me.

Holger

---

### Post by satimis on 2023-03-23
> **Holger_Gehrke said:**
> That's strange. A spelling dictionary for a writing system that uses ideograms ? Makes very little sense ... I tried it myself and got the same message; hit the 'close' button on the error message and marked part of my image for recognition, hit the recognize button, and recognition proceeded, producing a text panel full of symbols I wouldn't know how to enter (or read ...), not all - but most - of them identical to the ones in the image. What's especially strange about this is that I don't get an error like that when recognizing Japanese, which also uses ideograms (but also two syllabaries, so for words written using hiragana and katakana a spelling dictionary to enhance recognition would make some limited sense ...). Looks like a minor bug to me.

Holger
I have tried

My posting #5

2)
How To Convert Images To Text On The Linux Command Line With OCR
[https://www.howtogeek.com/devops/how-to-convert-images-to-text-on-the-linux-command-line-with-ocr/](https://www.howtogeek.com/devops/how-to-convert-images-to-text-on-the-linux-command-line-with-ocr/)

It is still the same.

Regards

---

### Post by Holger_Gehrke on 2023-03-23
> **satimis said:**
> 
2) How To Convert Images To Text On The Linux Command Line With OCR
[https://www.howtogeek.com/devops/how-to-convert-images-to-text-on-the-linux-command-line-with-ocr/](https://www.howtogeek.com/devops/how-to-convert-images-to-text-on-the-linux-command-line-with-ocr/)

It is still the same.


I'm not quite certain what you mean by that ...
If it's meant to be a question ('Is it still the same ?') in the sense of 'Would these instructions still work ?', then yes they would. You'd need to install the package 'tesseract-ocr' because gimagereader only installs the tesseract libraries, not the executable. And the command line version doesn't use dictionaries to enhance it's recognition, that's a feature of gimagereader. Instead of the '-l eng' for recognition of English text given in that tutorial you'd use '-l chi_tra' for Chinese traditional. And for pulling the image out of the PDF you'd need the package 'poppler-utils', which contains both pdftoppm - which the tutorial uses - and pdfimages - which I prefer.

One other thing: OCR programs in general and tesseract in particular are not good at reading coloured text on photographic background as shown in your image. At least use GIMP to change the images to greyscale and use the 'Colors'->'Level' tool to get a good contrast between text and background.

In gimagereader you can mark regions for reading and help tesseract avoid trying to recognize parts of the image that contain no text. The command line version has no such functionality and works best with straight text in simple layouts, for example a standard business letter is quite recognizable after OCR while a marketing brochure usually ends up needing a lot of manual work after OCR. There's few things as strange as the output generated by OCR from an image or part of an image that actually **is** an image.

Holger

---

### Post by satimis on 2023-03-23
> **Holger_Gehrke said:**
> I'm not quite certain what you mean by that ...
If it's meant to be a question ('Is it still the same ?') in the sense of 'Would these instructions still work ?', then yes they would. You'd need to install the package 'tesseract-ocr' because gimagereader only installs the tesseract libraries, not the executable. And the command line version doesn't use dictionaries to enhance it's recognition, that's a feature of gimagereader. Instead of the '-l eng' for recognition of English text given in that tutorial you'd use '-l chi_tra' for Chinese traditional. And for pulling the image out of the PDF you'd need the package 'poppler-utils', which contains both pdftoppm - which the tutorial uses - and pdfimages - which I prefer.
- snip -

$ tesseract -l chi_tra Kuoni_Presentation-0.png Kuoni_Presentation```

Error opening data file /usr/share/tesseract-ocr/5/tessdata/chi_tra.traineddata
Please make sure the TESSDATA_PREFIX environment variable is set to your "tessdata" directory.
Failed loading language 'chi_tra'
Tesseract couldn't load any languages!
Could not initialize tesseract.

```
The same error

Other advice noted and thanks

Regards

---

### Post by Holger_Gehrke on 2023-03-23
That's not the same error at all ! gimagereader couldn't find a dictionary, but what the command line version of tesseract is missing is the content of the tesseract-ocr-chi-tra package (basically data to allow tesseract to identify shapes as letters or characters). Are you using Ubuntu 22.10 or a beta of 23.04 ? Because the path to the file is for tesseract 5.x which is available starting with 22.10 but isn't available for 22.04. Check the version of tesseract with 'tesseract --version' (should output the version of tesseract and several of the libraries used by it), check the location of tesseract with 'which tesseract' ( perhaps the snap you tried brought a newer tesseract along ?) and take a look at /usr/share/tesseract-ocr/. If you've got a directory '4' in /usr/share/tesseract-ocr, then you somehow managed to have the program in version 5 but the data for version 4 and I don't know how that could happen.

Holger

---

### Post by satimis on 2023-03-23
> **Holger_Gehrke said:**
> That's not the same error at all ! gimagereader couldn't find a dictionary, but what the command line version of tesseract is missing is the content of the tesseract-ocr-chi-tra package (basically data to allow tesseract to identify shapes as letters or characters). Are you using Ubuntu 22.10 or a beta of 23.04 ? Because the path to the file is for tesseract 5.x which is available starting with 22.10 but isn't available for 22.04. Check the version of tesseract with 'tesseract --version' (should output the version of tesseract and several of the libraries used by it), check the location of tesseract with 'which tesseract' ( perhaps the snap you tried brought a newer tesseract along ?) and take a look at /usr/share/tesseract-ocr/. If you've got a directory '4' in /usr/share/tesseract-ocr, then you somehow managed to have the program in version 5 but the data for version 4 and I don't know how that could happen.

Holger
$ tesseract --version```

tesseract 5.3.0
 leptonica-1.82.0
  libgif 5.1.9 : libjpeg 8d (libjpeg-turbo 2.1.1) : libpng 1.6.37 : libtiff 4.3.0 : zlib 1.2.11 : libwebp 1.2.2 : libopenjp2 2.4.0
 Found AVX2
 Found AVX
 Found SSE4.1
 Found OpenMP 201511
 Found libarchive 3.6.0 zlib/1.2.11 liblzma/5.2.5 bz2lib/1.0.8 liblz4/1.9.3 libzstd/1.4.8
 Found libcurl/7.81.0 OpenSSL/3.0.2 zlib/1.2.11 brotli/1.0.9 zstd/1.4.8 libidn2/2.3.2 libpsl/0.21.0 (+libidn2/2.3.2) libssh/0.9.6/openssl/zlib nghttp2/1.43.0 librtmp/2.3 OpenLDAP/2.5.14

```

$ which tesseract```

/usr/bin/tesseract

```

$ ls -al /usr/share/tesseract-ocr/```

total 92
drwxr-xr-x   4 root root  4096 Mar 24 00:40 .
drwxr-xr-x 271 root root 12288 Mar 23 17:10 ..
drwxr-xr-x   3 root root  4096 Mar 20 17:24 4.00
drwxr-xr-x   3 root root  4096 Mar 24 00:40 5
-rwxr-xr-x   1 root root 34578 Dec 31  2019 language-specific.sh
-rwxr-xr-x   1 root root  4097 Dec 31  2019 tesstrain.sh
-rwxr-xr-x   1 root root 22352 Dec 31  2019 tesstrain_utils.sh

```

$ ls -al /usr/share/tesseract-ocr/4.00/```

total 12
drwxr-xr-x 3 root root 4096 Mar 20 17:24 .
drwxr-xr-x 4 root root 4096 Mar 24 00:40 ..
drwxr-xr-x 4 root root 4096 Mar 23 23:05 tessdata

```

$ ls -al /usr/share/tesseract-ocr/5/```

total 12
drwxr-xr-x 3 root root 4096 Mar 24 00:40 .
drwxr-xr-x 4 root root 4096 Mar 24 00:40 ..
drwxr-xr-x 4 root root 4096 Mar 24 00:40 tessdata

```

---

### Post by #&amp;thj^% on 2023-03-23
@ satimis, have you tried just opening said PDF in a browser, and copy what you need from there?
EDIT: If needed there is always Calibre, and poppler-utils

---

### Post by satimis on 2023-03-23
> **1fallen said:**
> @ satimis, have you tried just opening said PDF in a browser, and copy what you need from there?
EDIT: If needed there is always Calibre, and poppler-utils
Thanks for your advice.

No.  The .pdf file is a travel trip detail.  I must download it to read.  It is impossible reading it online.  I have contacted the Travel Agent

Regardsw

---

### Post by Holger_Gehrke on 2023-03-24
@1fallen: reread the thread. It was established rather early on that it's a PDF that contains only images, the kind of thing you get after running 'convert *jpg my.pdf'. satimis wants the text, but the file has the text as pixel based images of text. OCR is the only way to get the text.

@satimis: are you running a pre-release version of 23.04 ? Tesseract 5.3 is going to be part of that. Without seeing the contents of the directories '/usr/share/tesseract-ocr/4.00/tessdata/' and '/usr/share/tesseract-ocr/5/tessdata/' I can't be certain, but it looks like you've got a mix of binaries for tesseract 5 and data for tesseract 4, with the data for recognizing Chinese probably in '/usr/share/tesseract-ocr/4.00/tessdata/' where the program isn't expecting them. If the data format hasn't changed -which I doubt,since it's a major version change - you could try linking the files in '/usr/share/tesseract-ocr/4.00/tessdata/' into '/usr/share/tesseract-ocr/5/tessdata/' but I am not at all sure this will work.

Holger

---

### Post by satimis on 2023-03-24
> **Holger_Gehrke said:**
>  - snip -

@satimis: are you running a pre-release version of 23.04 ? Tesseract 5.3 is going to be part of that. Without seeing the contents of the directories '/usr/share/tesseract-ocr/4.00/tessdata/' and '/usr/share/tesseract-ocr/5/tessdata/' I can't be certain, but it looks like you've got a mix of binaries for tesseract 5 and data for tesseract 4, with the data for recognizing Chinese probably in '/usr/share/tesseract-ocr/4.00/tessdata/' where the program isn't expecting them. If the data format hasn't changed -which I doubt,since it's a major version change - you could try linking the files in '/usr/share/tesseract-ocr/4.00/tessdata/' into '/usr/share/tesseract-ocr/5/tessdata/' but I am not at all sure this will work.

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.2 LTS
Release:        22.04
Codename:       jammy

```

$ ls /usr/share/tesseract-ocr/4.00/tessdata/```

chi_sim.traineddata       chi_tra_vert.traineddata  osd.traineddata
chi_sim_vert.traineddata  configs                   pdf.ttf
chi_tra.traineddata       eng.traineddata

```

$ ls /usr/share/tesseract-ocr/5/tessdata/```

configs  pdf.ttf  tessconfigs

```

Whether you meant to run;```

$ ln -s /usr/share/tesseract-ocr/4.00/tessdata/ /usr/share/tesseract-ocr/5/tessdata/

```
???

---

### Post by Holger_Gehrke on 2023-03-24
> **satimis said:**
> 
Whether you meant to run;
```

$ ln -s /usr/share/tesseract-ocr/4.00/tessdata/ /usr/share/tesseract-ocr/5/tessdata/

```
???

Not quite.
```

sudo ln -s /usr/share/tesseract-ocr/4.00/tessdata/*.traineddata /usr/share/tesseract-ocr/5/tessdata/

```
That should put links to the language specific training data into the directory where tesseract 5 is looking for such data. But - as I said - it might not work since the data is for version 4.

But I still don't understand how you ended up with tesseract 5.3. A look at 'apt policy tesseract-ocr', please ?

Holger

---

### Post by satimis on 2023-03-24
> **Holger_Gehrke said:**
> Not quite.
```

sudo ln -s /usr/share/tesseract-ocr/4.00/tessdata/*.traineddata /usr/share/tesseract-ocr/5/tessdata/

```
That should put links to the language specific training data into the directory where tesseract 5 is looking for such data. But - as I said - it might not work since the data is for version 4.

But I still don't understand how you ended up with tesseract 5.3. A look at 'apt policy tesseract-ocr', please ?

Holger
$ sudo ln -s /usr/share/tesseract-ocr/4.00/tessdata/*.traineddata /usr/share/tesseract-ocr/5/tessdata/
[sudo] password for satimis: 
It went through without complaint.  Still I couldn't copy the text

$ apt policy tesseract-ocr```

tesseract-ocr:
  Installed: 5.3.0-1ppa1~jammy1
  Candidate: 5.3.0-1ppa1~jammy1
  Version table:
 *** 5.3.0-1ppa1~jammy1 500
        500 https://ppa.launchpadcontent.net/alex-p/tesseract-ocr5/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     4.1.1-2.1build1 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

```

---

### Post by Holger_Gehrke on 2023-03-24
Okay, so you installed it from a PPA. That explain the unusual version. So now we have two options:
[LIST]
[*]remove the language packs for tesseract 4 and install the the language pack for all language from the PPA (a package named 'tesseract-lang' if I understand the page at [https://launchpad.net/~alex-p/+archive/ubuntu/tesseract-ocr5](https://launchpad.net/~alex-p/+archive/ubuntu/tesseract-ocr5) right) 
[/LIST]
or


[LIST]
[*]remove tesseract 5, remove the PPA from your repositories and install tesseract 4 
[/LIST]
Either way, the links we created are no good, so the first thing to do either way is to remove them again.

> **satimis said:**
> Still I couldn't copy the text
Do you expect that you can just copy the text in a pdf viewer just because OCR is installed ? That's not the way that works, sorry. You still would have to split the PDF into images, start the OCR with each image file and generate a new pdf from the image and the recognized text ('tesseract -l chi_tra page01.jpg page01 pdf') and then when you have done this for all the pages you join the pages into one pdf file with pdfunite (another of the poppler-utils). Now you'd have a pdf with the graphics as the top layer and the recognized text hidden behind the image which allows to to select the text. That, by the way, is not the way I do it normally because such PDFs are big and the results when copying text from them are rather unpredictable because the text is not stored in the PDF in the order it appears on the page; when copying a larger portion you are likely to get a horrible jumble of pieces of the text. I normally extract to text files and rebuilt the layout in LibreOffice. Takes a lot longer but you get smaller PDF which work right with copy and paste.

Holger

---

### Post by Claus7 on 2023-03-24
Hello,

> **Holger_Gehrke said:**
> ...


Do you expect that you can just copy the text in a pdf viewer just because OCR is installed ? That's not the way that works, sorry. You still would have to split the PDF into images, start the OCR with each image file and generate a new pdf from the image and the recognized text ('tesseract -l chi_tra page01.jpg page01 pdf') and then when you have done this for all the pages you join the pages into one pdf file with pdfunite (another of the poppler-utils). Now you'd have a pdf with the graphics as the top layer and the recognized text hidden behind the image which allows to to select the text. That, by the way, is not the way I do it normally because such PDFs are big and the results when copying text from them are rather unpredictable because the text is not stored in the PDF in the order it appears on the page; when copying a larger portion you are likely to get a horrible jumble of pieces of the text. I normally extract to text files and rebuilt the layout in LibreOffice. Takes a lot longer but you get smaller PDF which work right with copy and paste.

Holger

I wasn't aware of the aforementioned technique. I had the impression that image pdf files were impossible to get converted to any form of text. Thank you for that.

Regards!

---

### Post by Holger_Gehrke on 2023-03-25
> **Claus7 said:**
> 
I wasn't aware of the aforementioned technique. I had the impression that image pdf files were impossible to get converted to any form of text. Thank you for that.


There's a reason it isn't done often or talked about much: the error rates of OCR still are on the order of 1 wrong character for every 100 to 1000 characters depending on the quality of the image (contrast and resolution are the most important factors), which works out to about 4 to 40 errors per page assuming a line length of 80 characters and 50 lines per printed page (even worse rates are common for things like multicoloured text on a photographic background). And since this technique produces PDF - which are not easily editable - correcting these errors is hard. Producing an intermediate text file and recreating the layout after correcting the text produces better results but is more work.

Holger

---

### Post by satimis on 2023-03-25
Hi all,

Lot of thanks for your advice.

This is an itinerary of a tour to Balkan prepared by the Travel Agent.  What I need are only the name of the countries, cities and spots to visit.  I don't need the activity details.

It would not be easier for me to re-type them rather than dragging along here.  Sorry, I won't continue further.  Anyway lot of thanks for all of you spending your time to help me. 

Regards

---

