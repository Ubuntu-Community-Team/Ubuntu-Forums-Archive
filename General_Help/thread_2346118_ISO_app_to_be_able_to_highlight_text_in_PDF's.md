---
title: "ISO app to be able to highlight text in PDF's"
date: 2016-12-11
forum: General Help
---

### Post by juntjoo2 on 2016-12-11
Any recommendations? I can do this with Adobe reader on my Android phone and would like to do the same in here.  Thanks

---

### Post by 1clue on 2016-12-11
You mean select it as in copy/paste, or highlight as in use a highlighter pen on paper to permanently mark the page?

---

### Post by juntjoo2 on 2016-12-11
the latter thanks

I'm trying to install Adobe Reader from instructions from this page: [http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader-deb-package-downloaded-from-adobe-website](http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader-deb-package-downloaded-from-adobe-website)
and I get this:

```
ben@Hal:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 acroread : Depends: nspluginwrapper but it is not installable
E: Unable to correct problems, you have held broken packages.
```

then down the page I'm working from was another solution dealing with downloading the deb from adobe and I got this error:

```
ben@Hal:~/Downloads$ sudo dpkg -i --force-architecture AdbeRdr9.5.5-1_i386linux_enu.debSelecting previously unselected package adobereader-enu:i386.
(Reading database ... 210682 files and directories currently installed.)
Preparing to unpack AdbeRdr9.5.5-1_i386linux_enu.deb ...
Unpacking adobereader-enu:i386 (9.5.5) ...
dpkg: error processing archive AdbeRdr9.5.5-1_i386linux_enu.deb (--install):
 trying to overwrite '/etc/bash_completion.d/acroread.sh', which is also in package acroread-bin:i386 9.5.5-1precise1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 AdbeRdr9.5.5-1_i386linux_enu.deb

```

Doesn't look good.  Is it impossible?  I don't even know if this will allow me to highlight text as I want but I'm just trying whatever til I find a solution.

---

### Post by dragonfly41 on 2016-12-11
Try [Foxit Reader]("https://www.foxitsoftware.com/products/pdf-reader/").
Also Okular allows text highlighting, but Foxit Reader has  features for adding notes linked to highlighting.

---

### Post by juntjoo2 on 2016-12-11
Thank you. I will check them out...

---

### Post by vasa1 on 2016-12-11
> **juntjoo2 said:**
> I'm trying to install Adobe Reader from instructions from this page: [http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader-deb-package-downloaded-from-adobe-website](http://askubuntu.com/questions/89127/how-do-i-install-adobe-acrobat-reader-deb-package-downloaded-from-adobe-website)
...
There are a few answers on that page. I think you need to following the instructions in [this answer which is "For Ubuntu 14.04 LTS, 16.04 LTS and 16.10, 32- or 64-bit"]("http://askubuntu.com/a/89129").

I don't need the program and so haven't tried the answer's procedure myself.

---

### Post by juntjoo2 on 2016-12-11
Thank you

Actually I just discovered that indeed with the doc viewer that comes with Ubuntu you can highlight text.  It just wasn't as easy as clicking a highlight option in the context menu after selecting some text.  The controls are elsewhere.

---

