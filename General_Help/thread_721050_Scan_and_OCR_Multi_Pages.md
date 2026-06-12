---
title: "Scan and OCR Multi Pages"
date: 2008-03-10
forum: General Help
---

### Post by Smoothice on 2008-03-10
I have installed Gusty and have been using it now for about a month.  I have played alot and learned even more.  I am thinking that I might be able to use this at work for a project I have been thinking about for some time but found no good solution in windows.

First off let me say I work for a trucking company.  We use individual numbered waybills to track shipments.  We currently have no imaging system and have to dig through boxes of these bills when we need to provide proof of deliveries.  This is very ineffiecient.  

What I would like to do in order is:
1) Do a daily scan of all of the waybills that were done for the day.  
2) I would then like to take this scan(could be up to 300+ pages) and slipt this into individual pages saved as something like a pdf or a tiff.  
3) I would then like to OCR each file and figure out the waybill number.  
4) I would then like to save the file using the waybill number.

I know this is alot to ask but being so new I do not know where to start to put together a few scripts to do this.  This would greatly advance a project I have been planning for a long time now.  This would be my greatest hurdle. If anyone can point me in t right direction for any of these steps it would be greatly appreciated.

Aaron

---

### Post by Irihapeti on 2008-03-11
I don't know if you'll find an OCR program that's totally accurate. The best I've seen is Tesseract, which is a command-line program (which would make it easy to incorporate into a script). The version in the Gutsy repositories is useless (on my machine at least).   I use version 1.03 which I compiled from source.  I've found it is very good with non-English text, which might be useful when you are dealing with numbers. There are later versions, but I've found them slightly less accurate.

I don't think it handles column-formatted text well. You'd need to try it out for yourself.

For further info see [http://ubuntuforums.org/showthread.php?t=361851&highlight=OCR](http://ubuntuforums.org/showthread.php?t=361851&highlight=OCR)

Xsane scanner can be set up to do incremental saves: doc001.tif, doc002.tif etc. That might take care of the scanning side of the operation.

---

### Post by Smoothice on 2008-03-11
Does anyone know if it possible to OCR a certain part of the waybill.  This could be set to scan just where the waybill number is.  Don't know if this is possible.  Any experts out there?

Aaron

---

### Post by Cadmus on 2008-03-11
Could you find the region of the page the text is in and then use some sort of command line image manipulator to crop it down to the part your interested in?

---

### Post by Smoothice on 2008-03-11
I need to have the full image.  I just need to OCR about 1/8th of the page.  It would be used to provide proof of deliveries.  Cutting the image down really wouldn't help in this case.

Aaron

---

### Post by Irihapeti on 2008-03-12
Any chance of generating the waybills on computer in the first place? Then there's no need to scan anything.

---

### Post by Smoothice on 2008-03-12
The waybills can't be done on the computer.  They follow the shipment and will have shipper, driver and receiver signatures as well as any notes that were made along the way.

Aaron

---

### Post by Cadmus on 2008-03-13
I realise I wasn't so clear, let's assume you've scanned your waybill as waybill.tif and you know to a reasonable accuracy the region where the number will be (in terms of coordinates in the image) could you not use mogrify or something to pass just the region you need to tesseract using a pipe like this?

```
mogrify waybill.tif --crop 300x50 100 500 | tesseract
```

---

