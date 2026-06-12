---
title: "ZEBRA LP-2844 6x4 label printer"
date: 2020-09-10
forum: General Help
---

### Post by suomalainen on 2020-09-10
I have been having problems getting my LP 2844 to produce nice clean labels. All the lines are squiggly.

I did find a ppd and installed it via system --> Admin -->Printers. But that didn't help. Even via CUPS the install failed too.

Has anyone ever used this label printer successfully and if so what did you do to make it work for you.

Thank you,

John

---

### Post by oldfred on 2020-09-10
Often Zebra needed RAW printed so all control codes come from application, not a print driver.

Zebra & raw print device:
[http://code.google.com/p/jzebra/](http://code.google.com/p/jzebra/)
[http://qzindustries.com/download](http://qzindustries.com/download)
[http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu](http://code.google.com/p/jzebra/wiki/TutorialRawUbuntu)
[https://qz.io/wiki/Setting-Up-A-Raw-Printer-in-Ubuntu-Linux](https://qz.io/wiki/Setting-Up-A-Raw-Printer-in-Ubuntu-Linux)
[http://qzindustries.com/TutorialRawUbuntu](http://qzindustries.com/TutorialRawUbuntu)

---

