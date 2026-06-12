---
title: "Install Adobe Reader in Ubuntu 13.10"
date: 2013-11-23
forum: General Help
---

### Post by btcinema on 2013-11-23
I just can't believe I wasted other 2 hours looking for: HOW to install Adobe Reader in Ubuntu 13.10. (64 arch.)

Please HELP! I did not found any working method on GOOGLE.

I can't believe this!

---

### Post by howefield on 2013-11-23
What version of Ubuntu are you using ?

Download the deb file from the Adobe website ?

[http://ubuntuhandbook.org/index.php/2013/09/ubuntu-13-10-quick-tip-install-adobe-reader/](http://ubuntuhandbook.org/index.php/2013/09/ubuntu-13-10-quick-tip-install-adobe-reader/)

---

### Post by startas on 2013-11-23
Never thought about going to adobes site ang just download it ? [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/) :D And adobe stoped developing linux version many years ago, as so did many other developers, so the versions of many pdf readers for linux is very old.

---

### Post by btcinema on 2013-11-23
I've downloaded It...  this does not resolve my problem. I specifient Ubuntu 13.10 (64)!

---

### Post by startas on 2013-11-23
So ? if it does not work, just download some 32 bit c libraries.

---

### Post by btcinema on 2013-11-23
I've downloaded It...  this does not resolve my problem. I specifient Ubuntu 13.10 (64)!
Broken Dependecies when I try to install :
Correcting dependencies... failed.
The following packages have unmet dependencies:
 adobereader-enu:i386 : Depends: libgtk2.0-0:i386 (>= 2.4) but it is not installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

I'm new to linux, ubuntu... And I can't believe It's so hard to install a pdf reader...

---

### Post by startas on 2013-11-23
Yeah, i know, especially if dont know how to read in english :D Just download libgtk2.0-0:i386 from synaptic or using terminal.

---

### Post by btcinema on 2013-11-23
Well Thank you for helping me..
What next.. Since it's not working!


>  libgtk2.0-0 : Breaks: libgtk2.0-0:i386 (!= 2.24.21-1ubuntu1~saucy1) but 2.24.22-1ubuntu1~saucy1 is to be installed
 libgtk2.0-0:i386 : Depends: libatk1.0-0:i386 (>= 1.32.0) but it is not going to be installed
                    Depends: libcairo2:i386 (>= 1.6.4-6.1) but it is not going to be installed
                    Depends: libcups2:i386 (>= 1.6.2) but it is not going to be installed
                    Depends: libfontconfig1:i386 (>= 2.9.0) but it is not going to be installed
                    Depends: libgdk-pixbuf2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                    Depends: libglib2.0-0:i386 (>= 2.37.3) but it is not going to be installed
                    Depends: libpango-1.0-0:i386 (>= 1.28.3) but it is not going to be installed
                    Depends: libpangocairo-1.0-0:i386 (>= 1.28.3) but it is not going to be installed
                    Depends: libpangoft2-1.0-0:i386 (>= 1.28.3) but it is not going to be installed
                    Depends: libx11-6:i386 (>= 2:1.4.99.1) but it is not going to be installed
                    Depends: libxcomposite1:i386 (>= 1:0.3-1) but it is not going to be installed
                    Depends: libxcursor1:i386 (> 1.1.2) but it is not going to be installed
                    Depends: libxdamage1:i386 (>= 1:1.1) but it is not going to be installed
                    Depends: libxext6:i386 but it is not going to be installed
                    Depends: libxfixes3:i386 but it is not going to be installed
                    Depends: libxi6:i386 but it is not going to be installed
                    Depends: libxinerama1:i386 but it is not going to be installed
                    Depends: libxrandr2:i386 (>= 2:1.2.99.3) but it is not going to be installed
                    Depends: libxrender1:i386 but it is not going to be installed
                    Breaks: libgtk2.0-0 (!= 2.24.22-1ubuntu1~saucy1) but 2.24.21-1ubuntu1~saucy1 is to be installed


---

### Post by coffeecat on 2013-11-23
@btcinema, a couple of thread which may help:

[http://ubuntuforums.org/showthread.php?t=2189235](http://ubuntuforums.org/showthread.php?t=2189235)

[http://ubuntuforums.org/showthread.php?t=2181100](http://ubuntuforums.org/showthread.php?t=2181100)

---

### Post by btcinema on 2013-11-23
1. sudo dpkg -i Adobe*
   sudo apt-get install -f   -> NOT WORKING

2. Installed GDEBY -> does not let me install adobe reader.deb...

3. sudo dpkg -i --force-architecture AdbeRdr9.5.5-1_i386linux_enu.deb && sudo apt-get -f install

.does not work...

Thanks to google:
ran this 2 commands:
[COLOR=#3366FF]sudo aptitude install libgdk-pixbuf2.0-0:i386
sudo aptitude install libgtk2.0-0:i386

and opened the deb which I've downloaded from Adobe by Selecting Linux -> etc...deb file 
Opened the file with Gdeby and this time all was good..
[/COLOR]

---

### Post by howefield on 2013-11-23
You may have a specific reason for wanting Adobe Reader, thats fine. There a pdf reader in the default Ubuntu installation, just mentioning :)

---

### Post by btcinema on 2013-11-23
Please let me know if there is another pdf reader for Ubuntu 13.10 (64) . What is it called...how can I install it fast.... I've spend 3 hours with this :((
Sorry:

Still stuck: /opt/Adobe/Reader9/Reader/intellinux/bin/acroread: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

---

### Post by howefield on 2013-11-23
Search the Ubuntu dash for evince.

---

### Post by coffeecat on 2013-11-23
+1 for using evince for basic pdf reading. But if you want something a bit more featured, okular is quite good and is in the repositories. It will pull in some KDE libraries but works well in Ubuntu with Unity. I always install it as one of my preferred applications.

---

### Post by btcinema on 2013-11-23
Thank You..
It only took 2 minutes :)....

---

### Post by nanog on 2013-12-19
> **coffeecat said:**
> +1 for using evince for basic pdf reading. But if you want something a bit more featured, okular is quite good and is in the repositories. It will pull in some KDE libraries but works well in Ubuntu with Unity. I always install it as one of my preferred applications.

Evince is feature poor and has very poor compatability with adobe pdfs. Okular also tends to fail with many pdf "forms" and/or complex pdfs.  


A big thank you to the OP!

---

### Post by dave2001 on 2014-02-27
I got the Adobe .deb to install fine, but it refused to run. The problem was solved by installing some libs:

```
sudo apt-get install libxml2:i386 libstdc++6:i386
```

I'm sure there are more libs which are required, these two happened to be the ones I was missing.

I've seen it suggested the following packages are are also needed: 

libgtk2.0-0:i386 
libgdk-pixbuf2.0-0:i386

These were already installed on my system though, so I don't know for sure.  I love Okular, but I needed Acrobat Reader for full support of xfa forms. Until we have an open-source program that does ***everything*** Acrobat does, there ought to be a sticky or a guide somewhere in the community docs for installing Acrobat Reader.  This is the current page in the Community Docs [https://help.ubuntu.com/community/AcrobatHowTo](https://help.ubuntu.com/community/AcrobatHowTo) and it is woefully inadequate.

---

### Post by coffeecat on 2014-02-28
> **dave2001 said:**
> Until we have an open-source program that does ***everything*** Acrobat does, there ought to be a sticky or a guide somewhere in the community docs for installing Acrobat Reader.  This is the current page in the Community Docs [https://help.ubuntu.com/community/AcrobatHowTo](https://help.ubuntu.com/community/AcrobatHowTo) and it is woefully inadequate.

The community in Community documentation includes everyone who uses Ubuntu. Which includes you. If you feel that strongly you are fully entitled to edit the page yourself. Good luck with that! :)

---

### Post by dave2001 on 2014-03-01
> **coffeecat said:**
> The community in Community documentation includes everyone who uses Ubuntu. Which includes you. If you feel that strongly you are fully entitled to edit the page yourself. Good luck with that! :)

That thought actually occurred to me as I was writing my last post but, having no experience contributing to the community doc's, didn't know where to start, and assumed contributers would be need to be part of some esoteric inner circle of Canonical initiates. Your post makes it sound as if it will be rather easy to get whatever "permissions" or "authorizations" I would need in order to do so. I'll certainly look into it now!

---

### Post by speartip on 2014-03-02
Just to chime in here I have just downloaded Master PDF Editor from here, it seems more feature rich than Evince.
[http://code-industry.net/free-pdf-editor.php](http://code-industry.net/free-pdf-editor.php)

---

