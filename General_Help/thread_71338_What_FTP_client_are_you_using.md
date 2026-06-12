---
title: "What FTP client are you using?"
date: 2005-10-03
forum: General Help
---

### Post by SilverTab on 2005-10-03
I need a secure (SSL/TLS) Ftp client with Distributed FTP support (PRET) on linux

so far I found NONE that offered both...list of what I tried so far:

gFTP: no support for SSL (as far as I can tell)
Secure FTP (java): just wasnt working...(couldnt connect on a FTP using SSL)
FlashFXP (wine): not working
Filezilla (wine): SSL works well (hurray), No PRET support
kftpgrabber: requires KDE headers...(I still haven't installed KDE...only some kde libs...not sure what I need to do in this case)
CuteFTP(wine) installer's not working
SmartFTP(wine): not fully working

any suggestions or am I doomed? At this point I dont care if it's a console app...
:confused:

---

### Post by SilverTab on 2005-10-03
ok I installed KDE completely and I am now using kftpgrabber (Best ftp client for linux I tried, closest one to flashfxp)

problem is...when I tried to install the package I got a dependency error...BUT the package installed anyway, and the app is running fine....


Still, the package is marked as a broken package and I cant install anything else unless I remove kftpgrabber....

if I try to apt-get install anything I get this error:

Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kftpgrabber: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
               Depends: libfontconfig1 (>= 2.3.0) but 2.2.3-4ubuntu7 is to be installed
               Depends: libidn11 (>= 0.5.13) but 0.5.2-3 is to be installed
               Depends: libqt3c102-mt (>= 3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



is there any way I can ignore the broken package since its working fine for me?

---

### Post by dcraven on 2005-10-03
Probably a stupid question, but did you run "apt-get -f install"?

Cheers,
~djc

---

### Post by KingBahamut on 2005-10-03
[QUOTE=SilverTab]I need a secure (SSL/TLS) Ftp client with Distributed FTP support (PRET) on linux
so far I found NONE that offered both...list of what I tried so far:
gFTP: no support for SSL (as far as I can tell)
Secure FTP (java): just wasnt working...(couldnt connect on a FTP using SSL)
FlashFXP (wine): not working
Filezilla (wine): SSL works well (hurray), No PRET support
kftpgrabber: requires KDE headers...(I still haven't installed KDE...only some kde libs...not sure what I need to do in this case)
CuteFTP(wine) installer's not working
SmartFTP(wine): not fully working
any suggestions or am I doomed? At this point I dont care if it's a console app...
:confused:[/QUOTE]

it may seem trite , but have you tried ncftp?

---

### Post by SilverTab on 2005-10-03
[QUOTE=dcraven]Probably a stupid question, but did you run "apt-get -f install"?
Cheers,
~djc[/QUOTE]

I tried...all it does is try to remove kftpgrabber:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  kftpgrabber
0 upgraded, 0 newly installed, 1 to remove and 82 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1905kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

---

