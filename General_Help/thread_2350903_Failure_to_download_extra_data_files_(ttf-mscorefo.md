---
title: "Failure to download extra data files (ttf-mscorefonts-installer)"
date: 2017-01-28
forum: General Help
---

### Post by johnstefnds on 2017-01-28
Every time I boot I get an update information window:

> Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.



When I click "run this action now" I get this in terminal:

> ^Attf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
0% [Working]


And terminal terminates itself 

I tried a sollution I saw on the web where I had to go to the git page and download all the .exe files and run a command to install them manually... the "update information" stop to appear for a day or two but I get it again...

What should I do?

---

### Post by Perfect Storm on 2017-01-28
See if this help:
```
sudo apt-get install --reinstall ttf-mscorefonts-installer  
```

and if it doesn't work you can get it manually:
```
wget http://httpredir.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb
sudo dpkg -i ttf-mscorefonts-installer_3.6_all.deb
```

---

### Post by T.J. on 2017-01-29
For myself, I ported over Debian 8's installer package, and replaced Ubuntu's in my workstation as it was faster than debugging 16.04's.   The Ubuntu package has download problems related to Sourceforge for some time - about a year - and has not been corrected.    Unless you need the Microsoft fonts for Wine or Steam, I would just remove the "ttf-mscorefonts-installer" package.

I can give you instructions on how to obtain a working package if you need it.

---

### Post by johnstefnds on 2017-01-29
> **Artificial Intelligence said:**
> See if this help:
```
sudo apt-get install --reinstall ttf-mscorefonts-installer  
```

and if it doesn't work you can get it manually:
```
wget http://httpredir.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb
sudo dpkg -i ttf-mscorefonts-installer_3.6_all.deb
```

I went with the first solution and everything seems to work fine for now if the problem doesnt reappear soon ill tag this as solved.

Thank you.

---

