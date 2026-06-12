---
title: "hp series 1510 scanning"
date: 2007-09-27
forum: General Help
---

### Post by patricianicca on 2007-09-27
i have 1510 all in one it does everything but scan nothing even comes up 
on screen when i push scan button .New to all this  !!!!!!reading alot  on internet no wiser . so can anyone help me solve this ? or will i unistall and reinstall:popcorn:

---

### Post by linuxwizard on 2007-09-27
Need to install Sane.
[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

[http://tldp.org/HOWTO/Scanner-HOWTO/index.html](http://tldp.org/HOWTO/Scanner-HOWTO/index.html)

---

### Post by eggdeng on 2007-09-27
Use the xsane image scanning programme in the graphics section of the Applications menu. (I have a 1510, works like a charm).

---

### Post by gobbles414 on 2007-09-27
Hi patricianicca,

I recommend [gscan2pdf]("http://gscan2pdf.sourceforge.net") over Xsane for scanning. I doubt that the scan button on your printer/scanner will work in either application though (you'll activate the scanner using the software). I personally installed ALL of the extras recommended by gscan as well as sane-utils and libsane-extras in the Synaptic Package Manager libsane-extras might help if you still want to use Xsane or if your scanner's driver isn't part of the default Ubuntu installation. **I also followed the instructions on the gscan website so that the program is recognized in the synaptic package manager and updates are available in the update manager.**

---

