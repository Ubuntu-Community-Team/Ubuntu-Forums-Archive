---
title: "About PDFtk server"
date: 2017-06-14
forum: General Help
---

### Post by satimis on 2017-06-14
Hi all,

Ubuntu 16.04

Is PDFtk server on Ubuntu repo?  

OR I have to download it on;
PDF Labs
[https://www.pdflabs.com/tools/pdftk-server/](https://www.pdflabs.com/tools/pdftk-server/)
?

But only the package for Red Hat Enterprise Linux and CentOS is available.  Please advise.

Thanks

Regards
satimis

---

### Post by &amp;KyT$0P# on 2017-06-15
This? - [https://packages.ubuntu.com/xenial/pdftk]("https://packages.ubuntu.com/xenial/pdftk")
```
apt-cache show pdftk
```

---

### Post by satimis on 2017-06-15
> **halogen2 said:**
> This? - [https://packages.ubuntu.com/xenial/pdftk]("https://packages.ubuntu.com/xenial/pdftk")
```
apt-cache show pdftk
```
Hi,

Thanks for your advice.

I have pdftk, pdfjam, pdflatex, etc. running here.  They are wonderful tools for editing .pdf files, unfortunately not many articles/documentation related found on Internet.  Is pdf server different from pdftk?  I'm aware pdftk pro having more features than pdftk

Regards
satimis

---

### Post by &amp;KyT$0P# on 2017-06-15
From [https://www.pdflabs.com/tools/pdftk-server/#build]("https://www.pdflabs.com/tools/pdftk-server/#build") -
> You can compile PDFtk Server from its source code. PDFtk Server is known to compile and run on ... [Ubuntu Linux]("http://packages.ubuntu.com/search?keywords=pdftk"),

PDFtk and PDFtk Pro look to be Windows-only.

---

### Post by satimis on 2017-06-15
> **halogen2 said:**
> From [https://www.pdflabs.com/tools/pdftk-server/#build]("https://www.pdflabs.com/tools/pdftk-server/#build") -


PDFtk and PDFtk Pro look to be Windows-only.

Noted and thanks

Regards
satimis

---

### Post by jaysprout on 2017-08-18
I just installed it on CentOS7 after many wild Bantha chases through Google. One of those chases, I read it was, indeed, possible to install on Ubuntu and I'm seriously considering wiping my CentOS installation and replacing it with Ubuntu ... if I can find confirmation that PDFtk works on Ubuntu.

I don't know about Pro but I totally get how you're confused with PDFtk vs PDFtk Server ... I think "PDFtk" is the GUI and "PDFtk Server" is the command line version.

---

### Post by vocx on 2017-08-18
> **jaysprout said:**
> I don't know about Pro but I totally get how you're confused with PDFtk vs PDFtk Server ... I think "PDFtk" is the GUI and "PDFtk Server" is the command line version.
This is basically correct.

The "pdftk" program is a command line utility. In Linux you just install it from the repository, and use it from the terminal.

However, their website is seemingly aimed at Windows users, so they show different versions: a command line utility (pdftk server), a graphical user interface (pdftk), and a pro GUI version (pdftk pro). As most people in Windows are used to graphical interfaces they stress the GUI pdftk, and pdftk-pro, instead of the command line version "pdftk server". However, in Linux most people recognize the power of using the terminal instead of clicking on the screen, especially for batch processing files.

So, that's it.

---

### Post by monkeybrain20122 on 2017-08-19
> **vocx said:**
> This is basically correct.

The "pdftk" program is a command line utility. In Linux you just install it from the repository, and use it from the terminal.

However, in Linux most people recognize the power of using the terminal instead of clicking on the screen, especially for batch processing files.



BTW there is a gui for pdftk called pdfchain. It is in the repo. It doesn't have all the options of pdftk, but good enough for most purposes.

---

