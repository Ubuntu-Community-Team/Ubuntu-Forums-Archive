---
title: "Can't print PDFs?"
date: 2013-01-15
forum: General Help
---

### Post by d4m1r on 2013-01-15
Hey guys, so I have a fairly new wireless Lexmark printer on my network that I am able to print to just fine via Firefox and LibreOffice for example under my 12.04 LTS 64 bit install but not within Evince....I open a PDF with the default viewer, the printer is already on, configured, and set as the default within the Printing app, but the print button is not enabled....It is greyed out and closing and reopening the PDF in Evince does not enable the button either....

The Firefox and Chromium can't open the PDF either so how do I fix Evince to work with my configured printer? I am aware there is a linux version of Adobe Reader but I do not want to use it.

---

### Post by d4m1r on 2013-01-16
Is anyone able to print PDF files under Ubuntu 12.04 LTS x64? If so, using what application and what kind of printer?

---

### Post by Impavidus on 2013-01-16
As a work-around: firefox should be able to open (most) PDFs. You can install the pdfjs plug-in or use the build-in version, which is disabled by default. To enable it, type "about:config" in the address bar, click the warning away, search for pdfjs and set pdfjs.disabled to false. For me it works most of the time. You may give it a try.

I've never had any problems with evince and printing pdf, but I use 32 bit. I can't help you with that. (FYI, it was on an older model HP)

---

### Post by d4m1r on 2013-01-16
> **Impavidus said:**
> As a work-around: firefox should be able to open (most) PDFs. You can install the pdfjs plug-in or use the build-in version, which is disabled by default. To enable it, type "about:config" in the address bar, click the warning away, search for pdfjs and set pdfjs.disabled to false. For me it works most of the time. You may give it a try.

I've never had any problems with evince and printing pdf, but I use 32 bit. I can't help you with that. (FYI, it was on an older model HP)

Thanks for the suggestion, but I have enabled that and Firefox is still not able to open the PDF....The page simply comes up blank with no error :confused:

---

### Post by d4m1r on 2013-02-26
Just an update that I got the native Firefox PDF viewer working now and luckily it is able to print PDFs if anyone is having the same issue with Evince...I have tried to even contact its developers but have not received any response back in over a month.

---

