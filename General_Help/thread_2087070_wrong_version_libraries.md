---
title: "wrong version libraries"
date: 2012-11-22
forum: General Help
---

### Post by a.kazemi on 2012-11-22
hi 
after more than 3 days struggling to repair my ubuntu 12.04 amd64 and fixing one problem and find another problem again, today I find out that in my system there is some libraries which are for ubuntu 12.1 and they have installed because I have ubuntu quantal (12.1) mirror enabled in my update sources.
the main problem which was exist is partial upgrade warning! and also when I want to install some packages which depend on 32bit libararies give me the error which says ia32-libs cannot be installed. when I tried to install ia32-libs and its dependencies I found out many of those dependencies exist in my system but they are not appropriate version!
when I tried to install those dependencies through synaptic I saw that they were installed before but the version is not for the Ubuntu 12.04 and they are for Ubuntu 12.1!

when I want to uninstall them and install appropriate version again the synaptic says it has to remove almost all of the packages in my system because many of them are depend on those libraries.
now is there any way to repair this issue?

---

### Post by ajgreeny on 2012-11-22
It may take a long time, and it may not even work, but try disabling the the 12.10 mirror repos in your sources, then using synaptic see if you can use the menu, Package ->Force version option for each of the problem libraries.

It may turn out to be far too difficult, but surely is worth a try.

---

### Post by a.kazemi on 2012-11-23
thanks for answer but it still want to remove many packages even when I force some versions
another solution?!

---

### Post by ajgreeny on 2012-11-23
Not that I know of, I'm afraid.

---

### Post by a.kazemi on 2012-11-24
I reinstall all the ubuntu again!

but know does anyone know how I can save my software packages to use them later for installation on another ubuntu?

---

### Post by ajgreeny on 2012-11-25
All, or most, of the packages you have personally installed, as well as updated packages should be in /var/cache/apt/archives.  Copy all the *.deb files from there to a USB flash drive, then on another machine or a re-installtion of the same one, you can copy from the USB back to the cache with ```
sudo cp /media/<[COLOR=RoyalBlue]*USB*[/COLOR]>/*.deb /var/cache/apt/archives/
``` using the real mountfolder for the [COLOR=RoyalBlue]USB[/COLOR] flash, of course.

I do this all the time for 4 machines I have to work with and have never had any problems.

---

### Post by a.kazemi on 2012-11-26
thank you very much dear friend I used it and worked fine.

---

