---
title: "Question on Tesseract OCR"
date: 2006-09-30
forum: General Help
---

### Post by Sagotis on 2006-09-30
Has anyone used this program, and if so how does it work?

This an OCR program developed by HP and then released sometime this year by Google to the open source community.

There is the Google site explaining their involvenment and reason to open source it: [http://google-code-updates.blogspot.com/2006/08/announcing-tesseract-ocr.html](http://google-code-updates.blogspot.com/2006/08/announcing-tesseract-ocr.html)

And here is the the SourceForge site for it: [http://sourceforge.net/projects/tesseract-ocr](http://sourceforge.net/projects/tesseract-ocr)

It would be cool if the Ubuntu devs got behind this project.

Sagotis

---

### Post by Sagotis on 2006-09-30
Bump!

---

### Post by koshari on 2007-02-18
i have compiled a working version of tesseract from source and it work very well. 

[http://www.ubuntuforums.org/showthread.php?t=361851&highlight=ocr](http://www.ubuntuforums.org/showthread.php?t=361851&highlight=ocr)

---

### Post by drpaul on 2007-02-18
Watch out. The install from the tarball doesn't copy the tessdata folder to operating bin dire

Paul

---

### Post by eeried on 2008-02-10
There's some good documentation -- though it's in French you might be able to get the gist and the script. Just change the version of the software. you can install tesseract and gscan2pdf: 

[http://ubunteros.tuxfamily.org/spip.php?article148](http://ubunteros.tuxfamily.org/spip.php?article148)
 
Here's the script
```
# !/bin/sh
## Script d&#8217;installation pour la M.-L. linonroot-dev ## par Leonux
## Téléchargement des paquets
wget http://download.tuxfamily.org/xcfaudio/tesseract/tesseract_2.02-1_i386.deb
wget http://downloads.sourceforge.net/gscan2pdf/gscan2pdf_0.9.19_all.deb
## Installation de tesseract_2.02-1_i386.deb (b52) et de gscan2pdf
sudo dpkg --unpack tesseract_2.02-1_i386.deb
sudo apt-get install -f
sudo dpkg --unpack gscan2pdf_0.9.19_all.deb
sudo apt-get install -f 
```

Before using the script update it. So go to this page, [http://download.tuxfamily.org/xcfaudio/tesseract/](http://download.tuxfamily.org/xcfaudio/tesseract/) and find the latest version of tesseract and replace the "2.02-1" in the script by the latest version number.  

Do the same for gscan2pdf using this page: 
[http://downloads.sourceforge.net/gscan2pdf/](http://downloads.sourceforge.net/gscan2pdf/)

After the install is complete (quite a few packages from the Ubuntu repos get installed), you need to do this in Gutsy:

```
sudo mkdir /usr/share/tesseract-ocr
```
```
sudo ln -s /usr/share/tessdata /usr/share/tesseract-ocr
```

Otherwise you get error messages.

If you want to use tesseract inside Xsane you need to use   xsane2tess, a tessarct wrapper for Xsane. The following page has a convenient script to install it:
[http://doc.ubuntu-fr.org/xsane2tess](http://doc.ubuntu-fr.org/xsane2tess)
Then you need to edit Xsane prefs > settings > OCR > xsane2tess -l fra (this is L, not I) if you need French -- adapt to your language. Here's the complete lists of language packs and code: 
[http://code.google.com/p/tesseract-ocr/downloads/list](http://code.google.com/p/tesseract-ocr/downloads/list)

It seems installing gocr is enough for the English language. Install it and then launch Xsane. You can add this in the prefs > Settings > OCR: gocr -f UTF8

I find easier to use OCR inside Xsane because I can select the zone I want to scan first. Tesseract gets confused if you scan a page with three columns. I've been experimenting with some Schubert Lieder with the German original, the French translation and the English translation, each in a column. Gscan2pdf outputs each line in columns 1,2,3 in one row, which is rather confusing.

OCR itself works rather well though you need to copy the text in OOo and correct it, both with OOo tool and manually since OOo doesn't always understand there's something wrong in "|l" instead of 2 L letters.

All in all, if you don't need to edit the text later on, it may be faster to scan the text as an image or a PDF image, and edit it in GIMP to remove what's useless...

cheers,

---

