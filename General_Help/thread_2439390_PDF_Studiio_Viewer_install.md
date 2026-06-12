---
title: "PDF Studiio Viewer install"
date: 2020-03-27
forum: General Help
---

### Post by pierreu1 on 2020-03-27
[COLOR=#666666][FONT=&amp]From [https://www.qoppa.com/pdfstudioviewer/download/#linux64](https://www.qoppa.com/pdfstudioviewer/download/#linux64), 

I downloaded the 64 version, ...

in terminal, moved the directory to Downloads where the file is and then typed sudo sh ./PDFStudioViewer_linux64.sh[/FONT][/COLOR][COLOR=#666666][FONT=&amp]. and I got an error message: 

[/FONT][/COLOR]sh: 0: Can't open ./PDFStudioViewer_linux64.sh.

What am I doing wrong?

Thanks.

---

### Post by Impavidus on 2020-03-27
Maybe you have to give the file execute permissions?

BTW, it's a somewhat weird method to install something: a shell script with 200MB of binary data embedded. They also provide a .deb file (the 64 bit Debian package). That's the preferred way to install stuff on Ubuntu. I'd try that first.

---

### Post by u666sa on 2020-03-27
sh ./PDFStudioViewer_linux64.sh.

You put a dot at the end of sh.


P.S. I prefer Okular for my PDF viewing on Linux.

---

### Post by pierreu1 on 2020-03-28
I did, but that did not work. I did follow the advice of using the deb file, instead. Thanks.

---

### Post by pierreu1 on 2020-03-28
I think I did, but that did not work. I did follow the advice of using the deb file, instead. Thanks.

---

### Post by pierreu1 on 2020-03-28
Sadly, the studio version does not support xfa form and I need this feature. So, I am interest in  [https://code-industry.net/free-pdf-editor/](https://code-industry.net/free-pdf-editor/) recommended here ([https://unix.stackexchange.com/questions/265845/pdf-reader-that-supports-xfa-forms-while-adobe-reader-for-linux-is-not-supporte](https://unix.stackexchange.com/questions/265845/pdf-reader-that-supports-xfa-forms-while-adobe-reader-for-linux-is-not-supporte)), but I am stuck at the DEB version to choose. Where can I see QT number/version I have? Thanks for your kind support.

---

### Post by kostkon on 2020-03-28
> **pierreu1 said:**
> but I am stuck at the DEB version to choose. Where can I see QT number/version I have? Thanks for your kind support.
If you are on 18.04, then the option *64 bit  For CentOS/RedHat 7.x, Ubuntu 14.x - 19.x -> master-pdf-editor-5.4.38-qt5.amd64.deb* should work without problems.

---

### Post by pierreu1 on 2020-03-29
Thanks. It worked. However, t was indicated on the website where it was recommended that the free version has most functionalities, but I could not edit the document to the degree that I need (I cannot add any picture, for instance). It is better than before though! Anyway, as the last resort, I downloaded wine, playonlinux and adobe acrobat reader. After a few hours, I was able to open the doc., make some changes, but not all changes required. I still cannot add pictures. It does not help that I get a messed up (no text) on buttons when I wanted to print and check/modify some preferences. I cannot even save the document.

Btw, I want to show you a screenshot of what I see, but when I press "add an image" in here, it asks me for a URL I did using google drive. But, it does not work. Do you have any idea of why this is going on? Usually, if one wants to add an image, one can go to one's drive and fetch it. 

I wish I was still on Windows. All this for just a PDF form. It is too bad. 

Anyway, thanks for your kind help and support.

[IMG]https://drive.google.com/file/d/1my-k4L7SiQz2h9aARnpT6FYXk8pY5uH9/view?usp=sharing[/IMG]

[IMG]https://drive.google.com/file/d/1my-k4L7SiQz2h9aARnpT6FYXk8pY5uH9/view?usp=sharing[/IMG][IMG]https://drive.google.com/file/d/1my-k4L7SiQz2h9aARnpT6FYXk8pY5uH9/view?usp=sharing[/IMG]

---

