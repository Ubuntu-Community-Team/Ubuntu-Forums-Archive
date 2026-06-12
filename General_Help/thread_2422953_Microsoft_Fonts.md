---
title: "Microsoft Fonts"
date: 2019-07-15
forum: General Help
---

### Post by sporanox2 on 2019-07-15
I am running 18.04 xubuntu. When I try to install Microsoft Fonts via  sudo apt-get install msttcorefonts, I have been getting a failure to download.  Is there something new or that has changed?

---

### Post by olduse78802 on 2019-07-15
Try ttf-mscorefonts-installer instead of msttcorefonts maybe that will work.

---

### Post by yetimon_64 on 2019-07-15
Try with the package name "ttf-mscorefonts-installer".

There is no installation candidate available with the package name you are trying there...
```
yetiman:~ $  apt-cache policy msttcorefonts
msttcorefonts:
  Installed: (none)
  Candidate: (none)
  Version table:
```

Whereas with "ttf-mscorefonts-installer" ... ```
yetiman:~ $  apt-cache policy ttf-mscorefonts-installer
ttf-mscorefonts-installer:
  Installed: 3.6ubuntu2
  Candidate: 3.6ubuntu2
  Version table:
 *** 3.6ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu bionic/multiverse amd64 Packages
        500 http://archive.ubuntu.com/ubuntu bionic/multiverse i386 Packages
        100 /var/lib/dpkg/status
```

I am posting this from Xubuntu 18.04 as well. Cheers, yeti.

Edit: ninja'd by olduse78802. :-)

---

### Post by sporanox2 on 2019-07-15
It still fails on Download running sudo apt install ttf-mscorefonts-installer .   It appears only to install a few of the fonts

[https://i.imgur.com/BfLDYJa.png](https://i.imgur.com/BfLDYJa.png)

---

### Post by wildmanne39 on 2019-07-15
Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

When posting code please post the text using code tags instead of images by using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by nought2 on 2019-07-15
An alternative method will give you the full range of MS fonts. 

You will need access to a system with Win10 installed. 
Font folder is located at C:\Windows\Fonts

This folder can be copied into your Ubuntu installation. 
The method is explained at many places on the web.
Eg. [https://www.makeuseof.com/tag/how-to-install-microsoft-core-fonts-in-ubuntu-linux/](https://www.makeuseof.com/tag/how-to-install-microsoft-core-fonts-in-ubuntu-linux/)

---

### Post by garvinrick4 on 2019-07-15
> sudo apt-get install ubuntu-restricted-extras
Use arrow buttons when asks to agree

---

### Post by Impavidus on 2019-07-16
It appears to be a common issue: [https://ubuntuforums.org/showthread.php?t=2422878](https://ubuntuforums.org/showthread.php?t=2422878)

It's not the first time that download of Microsoft fonts fails.

---

