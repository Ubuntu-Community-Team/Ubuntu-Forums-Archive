---
title: "Trying to install tesseract and leptonica 13.1"
date: 2013-11-15
forum: General Help
---

### Post by yoshimitsuspeed on 2013-11-15
Sometimes Linux and open source drives me mad. Two hours I have been trying to get a simple OCE setup on my computer. Should be so frikken simple. 

Finally I found [http://ubuntuforums.org/archive/index.php/t-1647350.html](http://ubuntuforums.org/archive/index.php/t-1647350.html)

I modified the sources to install the newer 3.02 tesserect. 
I finally got leptonica 1.67 installed and all went fine except it didn't do the checkinstall. I figured this should be fine. 

Then I moved on to installing tesseract and when it came to ./configure it tells me it can't find leptonica. I think maybe it's not a new enough version so finally I find 1.69 and install it as per the instructions in the above link but modifying them to work with 1.69. Everything seems to go fine. Again checkinstall doesn't respond but everything else does. 

Go back to my tesseract dir and try to ./configure again and it gives me the same damn warning. How do I get it to find leptonica?

---

### Post by yoshimitsuspeed on 2013-11-16
No ideas?

---

### Post by jfolsom2 on 2013-11-17
According to [http://packages.ubuntu.com/search?keywords=tesseract-ocr](http://packages.ubuntu.com/search?keywords=tesseract-ocr) and [http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=leptonica&searchon=names](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=leptonica&searchon=names)

Tesseract and Leptonica are both available in the Universe repository. 

Is there a reason you want to install from source?

---

### Post by yoshimitsuspeed on 2013-11-17
It doesn't show up in the 13.1 repo

---

### Post by jfolsom2 on 2013-11-18
Are you sure you have the "Universe" repository enabled? Because they are explicitly available on Saucy (13.10).

---

### Post by yoshimitsuspeed on 2013-11-18
Ugh, frikken Muon. 
It didn't show up in a search but finally got everything installed from the terminal. 
OCR feeder and YGAF recognize Tesseract but gscan2PDF still doesn't show any OCR engine available. 

OCR feeder says it will create a searchable PDF but but when I export and select searchable PDF it exports but does not appear to be searchable. 

That is all I'm trying to do. I want to scan a manual and convert it to search able PDF. 
Any help would be appreciated. Can't believe something so simple can be so hard to get functional.

---

### Post by yoshimitsuspeed on 2013-11-20
Still haven't resolved my latest problems. 
I tried removing gscan2pdf, tesseract and leptonica and then reinstalled them in the proper order. gscan2pdf still does not recognize tesseract. 

I still haven't figured out how to make OCRfeeder create a searchable PDF. It says it can but when I select the option it is not searchable. 

I am not dead set on either of those programs. I just want the fastest easiest way to scan to searchable PDF.

---

