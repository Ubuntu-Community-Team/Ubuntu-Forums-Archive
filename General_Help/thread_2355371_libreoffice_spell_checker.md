---
title: "libreoffice spell checker"
date: 2017-03-12
forum: General Help
---

### Post by Nailhac on 2017-03-12
I am having difficulty in getting spell check to work in libre office 5.3 with ubuntu 16.04. I have checked to see which dictionaries are installed which appear to be ok but spell checker does nothing other than advise me that the document spelling is OK when I know it is not. Any advise would be appreciated.:confused:

---

### Post by howefield on 2017-03-12
Just tested with the same results, to fix it I had to install the en-gb spell checker

```
sudo apt-get install libreoffice-l10n-en-gb
```
  
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  hunspell-dictionary-en-gb | myspell-dictionary-en-gb hyphen-en-gb libreoffice-grammarcheck-en-gb libreoffice-help-en-gb mythes-en-gb
The following NEW packages will be installed
  libreoffice-l10n-en-gb
0 to upgrade, 1 to newly install, 0 to remove and 0 not to upgrade.
Need to get 419 kB of archives.
After this operation, 2,534 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu zesty/main amd64 libreoffice-l10n-en-gb all 1:5.3.0~rc3-0ubuntu1 [419 kB]
Fetched 419 kB in 0s (1,265 kB/s)              
Selecting previously unselected package libreoffice-l10n-en-gb.
(Reading database ... 182362 files and directories currently installed.)
Preparing to unpack .../libreoffice-l10n-en-gb_1%3a5.3.0~rc3-0ubuntu1_all.deb ...
Unpacking libreoffice-l10n-en-gb (1:5.3.0~rc3-0ubuntu1) ...
Setting up libreoffice-l10n-en-gb (1:5.3.0~rc3-0ubuntu1) ...
```

And then go to System Settings > Language Support which will likely complain of missing/incomplete support, accept the updates and restart. You may not need to restart the machine but certainly LibreOffice if open.

---

### Post by Nailhac on 2017-03-12
Thanks howefield now up and running.

---

### Post by howefield on 2017-03-12
Cool, glad you got it sorted. 

Feel free to mark the thread as solved to aid others who might pass by. :)

---

