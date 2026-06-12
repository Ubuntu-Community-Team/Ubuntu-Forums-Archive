---
title: "ubuntu 7.10: Printing: Allways letter and wrong orientation on duplex printing"
date: 2007-10-24
forum: General Help
---

### Post by Henrik Manum on 2007-10-24
Dear all

I have a problem that the print always comes out as "letter" rather than "a4". In addition I cannot control the duplex printing, it is always comes out upside down and always duplex. After reading similar threads, I have tried the following without luck:

- deleting all printers
- setting 
     cat /etc/papersize 
      a4
- reinstalling the printers
- locale:
henriman@d620:~$ locale
LANG=no_NO.UTF-8
LC_CTYPE="no_NO.UTF-8"
LC_NUMERIC="no_NO.UTF-8"
LC_TIME="no_NO.UTF-8"
LC_COLLATE="no_NO.UTF-8"
LC_MONETARY="no_NO.UTF-8"
LC_MESSAGES="no_NO.UTF-8"
LC_PAPER="no_NO.UTF-8"
LC_NAME="no_NO.UTF-8"
LC_ADDRESS="no_NO.UTF-8"
LC_TELEPHONE="no_NO.UTF-8"
LC_MEASUREMENT="no_NO.UTF-8"
LC_IDENTIFICATION="no_NO.UTF-8"
LC_ALL=
henriman@d620:~$ 

- sudo dpkg-reconfigure libpaper1 

This does not help however. I am in need of using the printer at a regular basis, so any hints are warmly welcome.

Regards, Henrik Manum

---

