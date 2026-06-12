---
title: "scanner produces blank image"
date: 2008-02-11
forum: General Help
---

### Post by donkyhotay on 2008-02-11
I have an epson stylus photo RX500 printer/scanner combo. I have successfully used it many times in the past by just plugging it into my computer and using xsane. I recently had to reformat/reinstall ubuntu 7.10 on my system however this time when I attempt to use my scanner I get 'blank' images when I scan and after it scans my scanner locks up until I power it off and back on again. My scanner is correctly found and identified when I run "scanimage -L" (as well as within xsane) but the second I try to scan or even hit 'preview' it goes completely wonky. I've even tried a simple "scanimage > test.pnm" to see if that would help at all but it resulted in the exact same problem. Anyone out there have an idea as to whats wrong with it?

---

### Post by geraldm on 2008-02-11
Some scanners must have a firmware file to load.  If your previous OS version had such a file, and your new OS does not, then that would account for the results that you are getting.
If you have a backup of your previous OS, perhaps you could check the sane directories, and 
note which sane-backend version works and which does not work.

Gerald

---

### Post by donkyhotay on 2008-02-12
No firmware was required on my previous installs and the sane directories aren't something I backed up before it went down. I know it has to be a configuration issue because it works with no problems on another computer I have with ubuntu 7.10 installed and it worked on this same computer with my previous ubuntu 7.10 install. I've compared everything I can think of between the two computers but I can not figure out what sort of config files may be missing or incorrect.

---

### Post by donkyhotay on 2008-02-14
bumpety bump?

---

### Post by plucky on 2008-02-14
donkyhotay,

Found this [article](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_Photo_RX500) about your epson printer.

Hope this helps.

Good luck

---

