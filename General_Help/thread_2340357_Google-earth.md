---
title: "Google-earth"
date: 2016-10-17
forum: General Help
---

### Post by robelli on 2016-10-17
How do I install Google-earth and get it running correctly  i.e with all the photos showing . At the moment I can run GE but the photo's do not show up . Only a blank .A few versions back Ubuntu ran GE very well so why has it changed in this version Ubuntu 16.04 . Also is there a way to get up to date maps






Computer:     HP Compaq-dc7900
Memory:       2Gb
Processor:    Intel Core 2 duo CPU E8400 @3 Ghz
HDD:            150GB
O.S:             Ubuntu 16.04 64bit

---

### Post by HereInOz on 2016-10-17
Here are some instructions.  Good luck.

[http://skagitsignal.com/how-to-install-google-earth-64-bit-in-ubuntu-16-04-lts-x64/](http://skagitsignal.com/how-to-install-google-earth-64-bit-in-ubuntu-16-04-lts-x64/)

---

### Post by valereguerin on 2016-10-17
```
sudo apt-get update && sudo apt-get upgrade
``` 

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get dist-upgrade
``` 

go to Google-earth  originally Web site , take the .deb CHOOSE your architecture   (32 or 64 Bits)

```
sudo apt-get install gdebi
``` 

& install your Google-earth.deb with GDebi : (alt + F2) Gdebi

Be sure you have libfreeimage3 installed ! if not sudo apt-get install  libfreeimage3 before install your package ! Dependences...

```
sudo apt-get install -f
```

Enjoy !

):P

---

### Post by HereInOz on 2016-10-17
I just read your bit about up to date maps.  Tragically, that is determined by Google.  We have one area south of where I live in which the latest photograph is 2006.  It is a rural area so I guess they don't bother too much with it.  Urban areas are updated more regularly.  What you see is indeed what you get, and that is all there is available.

---

### Post by valereguerin on 2016-10-17
they (google photographers) can't be anywhere anytime for street view......maps update.....06/2015...for me...:     [http://imgur.com/a/Gd1hq](http://imgur.com/a/Gd1hq)

---

### Post by robelli on 2016-10-23
Sorry for delay in answering folks but my internet went down and has only just come back.
Hereinoz . The link you gave does not work for me
Valereguerin . Thank you for the instructions . Followed them and have now got GE working great
Thanks all for your help .
:D





Computer:     HP Compaq-dc7900
Memory:       2Gb
Processor:    Intel Core 2 duo CPU E8400 @3 Ghz
HDD:            150GB
O.S:             Ubuntu 16.04 64bit

---

