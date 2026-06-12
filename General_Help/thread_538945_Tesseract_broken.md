---
title: "Tesseract broken"
date: 2007-08-30
forum: General Help
---

### Post by sumone on 2007-08-30
Tesseract has installed as part of Fiesty however it does not appear in any menu. If I try to run it from the terminal I get the following error:
david@ukasia:~$ tesseract
tesseract:Error:Usage:tesseract imagename outputbase [configfile [[+|-]varfile]...]

Signal_exit 25 ABORT. LocCode: 3  AbortCode: 0
david@ukasia:~$ 

Could someone kindly tell me what this means

thanks

---

### Post by Irihapeti on 2007-09-09
Tesseract is a command-line application. You need to have a .tif file with your text in it already scanned. Then type tesseract <filename>.tif <outputfilename>, where <filename> is your scanned image and <outputfilename> is the text file you will end up with.

If you find you get junk instead of a readable output, you might like to look at
[http://ubuntuforums.org/showthread.php?t=361851](http://ubuntuforums.org/showthread.php?t=361851)

Tesseract has now migrated to [http://code.google.com/p/tesseract-ocr/](http://code.google.com/p/tesseract-ocr/) and there's a later version that I'm just downloading now.

HTH
Irihapeti

---

### Post by ricardisimo on 2008-05-08
Compiling the new version (2.03, I believe) seems to be different from earlier versions... something about there being two tarballs, and where to put which ahead of time, and I don't know what else. Could someone walk me through the install? Thanks.

---

