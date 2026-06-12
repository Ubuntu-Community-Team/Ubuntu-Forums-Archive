---
title: "cups browsing protocol unsupported in ubuntu 18.04"
date: 2019-01-15
forum: General Help
---

### Post by rmstock2 on 2019-01-15
I installed 18.04 and no doubt is a great improvement over 16.04.
I wanted to print, but cups had failed to automatically add the printers from my old cups server.
lpstat -t comes up empty.    cups  2.2.7-1ubuntu2.2 amd64 is installed.
checking the cups error log showed a strange error :

"Unknown browse protocol "cups" ignored."  How strange is that ?

[https://i.imgur.com/lbJcp0D.png](https://i.imgur.com/lbJcp0D.png)

---

### Post by rmstock2 on 2019-01-15
It seems cups printing has since 2016 become an  Apple game :

```

 SEE ALSO
       backend(7), classes.conf(5), cups(1), cups-files.conf(5),  cups-lpd(8),
       cupsd.conf(5),  cupsd-helper(8),  cupsd-logs(8), filter(7), launchd(8),
       mime.convs(5), mime.types(5), printers.conf(5), systemd(8), CUPS Online
       Help (http://localhost:631/help)


COPYRIGHT
       Copyright © 2007-2017 by Apple Inc.


12 February 2016                     CUPS                             cupsd(8)

```

---

### Post by wildmanne39 on 2019-01-15
That is what my research shows as well, not that it is relevant to your issue.

---

### Post by rmstock2 on 2019-01-16
I installed the cups printing engine from 16.04 on bionic 18.04 :

cups : [ftp://ftp0.crashrecovery.org/pub/linux/cups/DEB/ubuntu1804/](ftp://ftp0.crashrecovery.org/pub/linux/cups/DEB/ubuntu1804/)
poppler : [ftp://ftp0.crashrecovery.org/pub/linux/cups/DEB/ubuntu1804/poppler/](ftp://ftp0.crashrecovery.org/pub/linux/cups/DEB/ubuntu1804/poppler/)
cups-filters : [ftp://ftp0.crashrecovery.org/pub/linux/cups/DEB/ubuntu1804/cups-filters/](ftp://ftp0.crashrecovery.org/pub/linux/cups/DEB/ubuntu1804/cups-filters/)


And printing works all right now :

[IMG]https://i.imgur.com/tpL8R17.png[/IMG]

---

### Post by him610 on 2019-01-16
> It seems cups printing has since 2016 become an Apple game

Possibly, however, those of us who use open source software should also thank Apple.
From [https://www.cups.org/]("https://www.cups.org/")
 CUPS is the standards-based, open source printing system **developed by Apple Inc.** for macOS® and other UNIX®-like operating systems.

---

### Post by rmstock2 on 2019-01-18
> 
[COLOR=#000000]CUPS is the standards-based, open source printing system [/COLOR]**developed by Apple Inc. for macOS® and other UNIX®-like operating systems.**


Not quite :

```

SEE ALSO
       backend(1),  classes.conf(5),  cupsd.conf(5), filter(1), mime.convs(5),
       mime.types(5),  printers.conf(5),  CUPS  Implementation  of  IPP,  CUPS
       Interface  Design  Description,  CUPS  Software  Administrators Manual,
       http://localhost:631/documentation.html


COPYRIGHT
       Copyright 1993-2003 by Easy Software Products, All Rights Reserved.


18 July 2002              Common UNIX Printing System                 cupsd(8)

```

[URL="https://en.wikipedia.org/wiki/Easy_Software_Products"]**Easy Software Products - Wikipedia**


[/URL][https://en.wikipedia.org/wiki/Easy_Software_Products](https://en.wikipedia.org/wiki/Easy_Software_Products)

---

