---
title: "Cannot get printer work"
date: 2015-05-23
forum: General Help
---

### Post by andfree on 2015-05-23
Lubuntu 14.04 LTS is installed to the laptop, but I let the thread without prefix, because I remember I had the same problem on Ubuntu, too. 

I connected Konica Minolta magicolor 4650 on USB port and installed the recommended driver (it was for 4690, there was not one for 4650). I try to print test pages, but it prints only some unwanted symbols at the upper left of the page (some smiles, a "X", some squares, a rhomb) and the rest of the page remains blank. Amy ideas what to do? Thanks.

---

### Post by Easy Limits on 2015-05-23
In my experience, if you don't see the exact model number of the printer you are trying to install you are going to have lots of difficulty.

---

### Post by ian-weisser on 2015-05-23
1) Get the proper PPD file tarball from [http://printer.konicaminolta.com/support/current_printers/mc4650_sup.htm#Drivers](http://printer.konicaminolta.com/support/current_printers/mc4650_sup.htm#Drivers)

2) Select the proper PPD file (language and printer model) and extract it from the tarball.

3) Install the PPD file by placing it in /etc/cups/ppd . Change the file's ownership to root:root, just like all the other PPD files in that directory.
Example:
```
$ ls -l /etc/cups/ppd/
-rw-r--r-- 1 root root  49954 Mar 26 16:11 OKM480.ppd
```

4) Edit the printer settings in CUPS to use the proper PPD file.

---

### Post by andfree on 2015-05-23
Thanks to both of you for the replies.

Ian-weisser, you solved my problem. M4650opn.ppd got the job done. Thanks a lot.

---

