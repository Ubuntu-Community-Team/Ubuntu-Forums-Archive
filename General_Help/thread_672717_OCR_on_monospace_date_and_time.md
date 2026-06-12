---
title: "OCR on monospace date and time"
date: 2008-01-19
forum: General Help
---

### Post by susscorfa on 2008-01-19
Hi i have about a 10000 pictures containing some data i have to get out, the data is displayed in the upper row and looks like the attached picture. I have inverted the colors and removed the rest of the picture. I'm planning to automate this with imagemagic or something comparable. The problem is to get proper OCR (optical character regoniztion). I have played around with tesseract, ocrad and gocr the last one works best and i got it up to the following.

```
$ gocr -d 0 -l 160 -m 32 -C "1234567890AMP:/C-" small.pnm 
2000_01_10 5__09__50 PM   M 1/10                   _  310C

```

But does any one see away to improve on this because this is not good enough especialy 8 and 0 get mixed up. I don't get how i can improve tesseract but i saw some positive reviews of it. The other thing i was thinking if i could configure it in such a way that the program could use the information that it is a monospace font

---

### Post by susscorfa on 2008-01-20
some extra information

The text i have to analise is every time very compairable so date time picture number and a temperature.

---

### Post by susscorfa on 2008-01-20
By now i have everything ok exept for the fact that i still can't seperate a 8 from a 0. could anyone give a sugestion to improve?

---

### Post by SlithyTove on 2008-02-03
It is possible to train tesseract to[ recognize a particular font]("http://code.google.com/p/tesseract-ocr/wiki/TrainingTesseract"). I don't know enough about gocr to know whether it can be trained. BTW, [this review]("http://www.mscs.dal.ca/~selinger/ocr-test/") seems to show that tesseract does a much better job than the other two alternatives.

---

