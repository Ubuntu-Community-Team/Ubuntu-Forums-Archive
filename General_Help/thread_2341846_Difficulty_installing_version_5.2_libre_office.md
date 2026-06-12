---
title: "Difficulty installing version 5.2 libre office"
date: 2016-11-01
forum: General Help
---

### Post by Nailhac on 2016-11-01
I have attempted to install libre office 5.2 but cannot get passed the ubuntu single sign in account for ubuntu one. Is there a way of installing this prog via a sudo snap in terminal. I would appreciate any advice. I understand that ubuntu one has a bug when accessing it via the method I have tried.
Thanks in advance

---

### Post by Bucky Ball on 2016-11-01
You are running 14.04? Any burning reason you are wanting to upgrade to a newer version? Which version do you have installed now? What differences are you expecting?

What's wrong with downloading it from [the Libreoffice website]("https://www.libreoffice.org/download/libreoffice-fresh/?version=5.2&lang=en-US")? No doubt there's a PPA for it somewhere as well. How well it's going to run on whatever earlier version of Ubuntu you are using is another question.

---

### Post by vasa1 on 2016-11-01
LibreOffice 5.2 is available via a ppa:
For trusty, see [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty)
For xenial, see [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=xenial](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=xenial)
etc.

---

### Post by ajgreeny on 2016-11-01
> **vasa1 said:**
> LibreOffice 5.2 is available via a ppa:
For trusty, see [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=trusty)
For xenial, see [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=xenial](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=xenial)
etc.
And I have been using the ppa for a long time, maybe 2 or 3 years, with no problems of any sort on my Xubuntu 14.04.

Currently on LO Version: 5.2.3.2 and working great for me.

[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) for the complete ppa site which you can add by following the instructions there.

If it should happen to go wrong use **ppa-purge** package in the repos to remove that ppa and reinstall with the standard repos version of LO.

---

### Post by Bucky Ball on 2016-11-01
I stand corrected. :)

---

### Post by deadflowr on 2016-11-01
The bug of unable to login correctly to U1 on Ubuntu software affects only 16.04 and 16.10, since those are the only ones that have snaps and also show snaps via the software center/ Ubuntu Software (now gnome-software).
You can definitely run a snap command via the terminal to install the package:
First use snap find package name, like so
```
snap find libreoffice
```
to double check the name, so you don't try installing some other package that might have a similar name.
Then run the install command:
```
sudo snap install libreoffice
```

Note, unlike a ppa since snaps are isolated from the main system, you will have access to two different versions of libreoffice.

Some will probably tell you that you need to login, but I think that is only necessary for paid snaps
Run the command
```
 snap help
``` 
a quick listing of snap options.

Also, here's the bug ftr: [lpbug]1616943[/lpbug]

Hope it helps

---

