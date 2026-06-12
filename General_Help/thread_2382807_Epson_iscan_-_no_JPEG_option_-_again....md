---
title: "Epson iscan - no JPEG option - again..."
date: 2018-01-17
forum: General Help
---

### Post by 2CV67 on 2018-01-17
I have been using my Epson Perfection V200 Photo scanner in Ubuntu with Epson's iscan drivers since 2008.
With various problems after most updates!
My main OS is 17.10 & the scanner works OK there (with iscan_2.29.3-1~usb0.1.ltdl7_amd64.deb)

I just did a fresh install of 16.04LTS (backup system) & installed the current version of iscan (2.30.2-2_amd64.deb).
Everything seems OK except I can't save as JPEG.
I get the options PCX/PNM/PNG/TIFF/PDF but the JPEG option is grayed out.

I had similar problems back in 2010/2011 but the answer then was to update to the latest iscan, so that's out.

Thanks for any suggestions!

---

### Post by 2CV67 on 2018-01-18
I asked Epson for help & they sent me a standard reply with links to FAQs & Manuals etc.
The FAQs included a "no jpeg" problem from 2009/2011 & the answer was:
"Saving to JPEG is disabled when a compatible version of the JPEG library is not detected on your system. Please install libjpeg version 6 in order to restore the ability to save to JPEG."

Synapt shows me I already have libjpeg8 & libjpeg-turbo8 installed.
Libjpeg9 & libjpeg62 are available but not yet installed.

Assuming it could do no harm, I installed libjpeg9 & libjpeg62.

The scanner now saves to JPEG OK.
I don't know which libjpeg did the trick.
I don't know how you are supposed to know which you need.
I wonder why there are so many options & no information...

Anyway [SOLVED]

---

### Post by bnoeafk2 on 2018-11-08
With Ubuntu 18 (bionic) it was libjpeg62 that bought the JPEG capability back (using Image Scan for Linix 2.30.3)
> sudo apt-get install -y libjpeg62

---

### Post by neuman1812 on 2019-06-06
Just want to say thank you.  This resolved my issue for an Epson v370 on Ubuntu 18.04.  

Installing libjpeg62  got me back the jpeg option.

---

