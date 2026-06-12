---
title: "Libreoffice 32 bit or 64 bit"
date: 2016-09-12
forum: General Help
---

### Post by Hewjr100 on 2016-09-12
Just wondering if libreoffice in ubuntu 16.04 is 32 bit or 64 bit.

Henry

---

### Post by QIII on 2016-09-12
Hello!

Are you running the 32bit or 64bit version of Ubuntu?

---

### Post by DuckHook on 2016-09-12
I freely admit that what follows is nothing more than an educated guess, but I am willing to bet money that:

64-bit Ubuntu comes with 64-bit Libreoffice
32-bit Ubuntu comes with 32-bit Libreoffice

Not to pry, but why do you wish to know?

---

### Post by Hewjr100 on 2016-09-12
Running 64 bit, but in about section it does not specify.  In windows 10 I installed libreoffice 64 bit from ftp site.

Henry

---

### Post by QIII on 2016-09-12
[This]("https://launchpad.net/ubuntu/xenial/+source/libreoffice") indicates which packages are available.

64-bit is included.  If you install from the repo when you are running a 64 bit version of Ubuntu, by default you will install the 64 bit version of LO.

---

### Post by Hewjr100 on 2016-09-12
Here is what happened.  I installed LO from main website on windows 10.  In about section of LO it only listed version number, 5.2.1.2 it think.  I went to LO ftp site and found 64 bit version and installed it over other version.  Now about LO gives version number and x64 next to it.  In ubuntu there is no indication in about LO if its 32 or 64 bit.

Henry

---

### Post by DuckHook on 2016-09-12
There is a fundamental difference between Linux and Windows that goes to the core of what each OS is about and it affects the very essence of how apps are distributed, installed and used. In proprietary space, apps are by default private only-by-permission silo-ed things, so you have to go to each individual vendor website (their own silo) to download and install them, usually after making some form of payment. Since FOSS software is the polar opposite of this dynamic, there is no need (nor, indeed, any point) to keep them locked up in vendor controlled silos, so they are made available in the repos maintained by almost every distro out there.

The distro maintainers usually provide the further service of making sure that the apps are reasonably current, patched, original, free of malware, signed and (this is what you are interested in) the right architecture for the version of OS you are running. This is just one of many reasons that I find Ubuntu/Linux so convenient&#8213;I don't have to hunt all over the place for Linux apps&#8213;wondering if I have been suckered into a black site masquerading malware as a legitimate app. In the case of LO, the maintainers will already have ensured that the proper architecture has been matched to their distro.

---

### Post by vasa1 on 2016-09-12
> **Hewjr100 said:**
> Here is what happened.  I installed LO from main website on windows 10.  In about section of LO it only listed version number, 5.2.1.2 it think.  I went to LO ftp site and found 64 bit version and installed it over other version.  Now about LO gives version number and x64 next to it.  In ubuntu there is no indication in about LO if its 32 or 64 bit.

HenryIt's true that "about" doesn't provide information about whether LibreOffice is 32- or 64-bit. If you install LibreOffice from the official repos, you'll get the appropriate version. So why worry?

BTW, even Firefox doesn't show whether it's 32- or 64-bit in its "about"

Also, unless you know what you're doing, you're safer installing software from the official repos rather than any FTP site. All the same, when you visit LibreOffice's download page, you may see something like what's in the attached image. I have to take care to download what _*I*_ want and not what's offered by default. Note the "x64".

---

### Post by howefield on 2016-09-13
If the log hasn't archived you could try

```
cat /var/log/apt/history.log | grep "libreoffice"
```

:amd64 at the end of each package name will tell you that it is 64 bit.

---

### Post by Hewjr100 on 2016-09-13
Ok got it.  Was going to install 64 bit from LO ftp site, but that won't be needed.

Henry

---

