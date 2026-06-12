---
title: "Wine"
date: 2004-11-13
forum: General Help
---

### Post by Ozitraveller on 2004-11-13
Has anyone installed Wine from the Universe? If so are there any problems?

---

### Post by zenwhen on 2004-11-13
I had no issues at all. Go for it, if you have a use for it.

---

### Post by Ozitraveller on 2004-11-13
At the moment I'm just experimenting. I want to see whether MS Access 2000 will run in wine.

Thanks

---

### Post by calamari on 2004-11-27
Didn't work so well for me.. everything I run gives a Segmentation fault, error 139.  For example:

calamari@AMD1:~ $ wine /mnt/win98/windows/sol.exe
/usr/bin/wine: line 474:  9371 Segmentation fault      $WINEBIN/$WINE_BIN_NAME $DASH "$@"
Wine failed with return code 139

calamari

EDIT [Dec 22, 2004]:  The solution to my problem was to NOT use my old Windows registry.. apparently I have something icky in there and it's confusing wine.  It messes up a few apps, though, of course.. I'm going to attempt to export a small branch of the windows registry and reimport it into wine (using wine regedit.. so cool :)), then maybe textpad and winrar will be registered again.

---

### Post by wallijonn on 2004-12-03
exactly how does one get wine to install an MSOffice app?

starting a root terminal and saying wine /media/cdrom1/setup.exe just hangs my PC.

---

### Post by jdodson on 2004-12-03
[QUOTE=wallijonn]exactly how does one get wine to install an MSOffice app?

starting a root terminal and saying wine /media/cdrom1/setup.exe just hangs my PC.[/QUOTE]

[http://ubuntuforums.org/showthread.php?t=7025](http://ubuntuforums.org/showthread.php?t=7025)

---

### Post by wallijonn on 2004-12-03
I tried CXOffice (the install sh script you suppied) and wine. The CXoffice script seems to install correctly (adds to the Applications menu). But, just as in wine, it seems to switch over to a blank screen and cont-alt-f1 or f2 will not switch over to a new X screen.

---

