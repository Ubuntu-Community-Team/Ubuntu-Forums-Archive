---
title: "My state has made its 1040 tax form unprintable"
date: 2022-03-18
forum: General Help
---

### Post by lou6 on 2022-03-18
I've been able to print my state tax form for the last 10 years but not this year.  My state has made form 1040 unprintable. I tried qpdfview, Okular, Document Viewer and Atril with no joy at all.  I finally found a blank 1040 that would print and did the job with a pen...

The Linux version of Adobe hasn't been updated for 9 years - is there an alternative that I've missed?

Thanks for any help

---

### Post by dragonfly41 on 2022-03-18
Foxit  ?
or MasterPDF Editor ?
or Pandoc  (command line) ?

---

### Post by HermanAB on 2022-03-19
This is a common problem. Here is the solution:
[https://www.aeronetworks.ca/2021/04/unlock-cra-pdf-forms.html?m=1](https://www.aeronetworks.ca/2021/04/unlock-cra-pdf-forms.html?m=1)

---

### Post by lou6 on 2022-03-22
I tried Qpdf with great anticipation but it did not do the job.  My 1040 tax form will not print.  I guess my state assumes that everyone uses Windows and has invested in Adobe Acrobat...

---

### Post by wyattwhiteeagle on 2022-03-22
Try atril document viewer

```
sudo apt install atril
```

It's for Ubuntu-MATE but it came default on Xubuntu 20.04.

I've used it to view pdf's but can't say anything about printing them.

---

### Post by HermanAB on 2022-03-22
Come to think of it, PDF printing is part of CUPS.  You should be able to simply send the file to the printer:
$ lpr -P localhost file.pdf

That works for me.

---

### Post by lou6 on 2022-03-22
Tried lpr with no joy.  I also tried loading the 1040 file into LibreOfficeDraw and printing from there - that did not work either.

Thanks to all for your suggestions...

---

### Post by dragonfly41 on 2022-03-22
tesseract (optical character recognition - OCR) comes to mind,

[https://www.geeksforgeeks.org/python-reading-contents-of-pdf-using-ocr-optical-character-recognition/](https://www.geeksforgeeks.org/python-reading-contents-of-pdf-using-ocr-optical-character-recognition/)

---

### Post by Autodave on 2022-03-22
Xubuntu 20.04 here and I can print pdfs with no problem.  No other programs added.

---

### Post by MAFoElffen on 2022-03-22
'qpdf' works to unlock secured pdf files... The link posted above only has install instructions for RHEL branch Linux derivatives. Ubuntu has the package 'qpdf', but is in the Universe Repo.
```

sudo apt update
sudo apt install software-properties-common  # This package includes add-apt-repository
sudo apt-add-repository universe
sudo apt install qpdf
qpdf --decrypt lockedfile.pdf unlockedfile.pdf

```
As an alternative, I have used screenshot to capture the displayed, locked pdf, as a graphics file, inserted it into a LibreOfiice Doc file, then exported as a new PDF.

---

### Post by lou6 on 2022-03-23
I followed MAFoElffen's instructions to the letter but my 1040 will not print - only the top few lines (my name. address, etc.) print - the body of the form is blank.  My state has somehow used Adobe to prevent printing...

Tried Okular, Qpdfview, Atril and Document Viewer - none of these will print.

Thanks again to all who replied -

---

### Post by dragonfly41 on 2022-03-23
If you can read it by eyeball you can grab it and apply ocr.

tesseract as I wrote earlier.

---

### Post by lou6 on 2022-03-23
dragonfly41 - I wasn't snubbing you - all replies are appreciated.  I went to the link you posted and it seemed to be about Python libraries so I did not see how that would apply to printing a form encrypted by Adobe.  I have already filled out (by hand) and mailed my 1040 so I'll leave this problem until next year :)

---

