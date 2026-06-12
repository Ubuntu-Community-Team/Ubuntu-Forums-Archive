---
title: "About equery command"
date: 2006-11-06
forum: General Help
---

### Post by satimis on 2006-11-06
Hi folks,

ubuntu-6.06.1-LAMP-server-amd64

Please advise which package-tool provides "equery" command


$ sudo apt-cache search equery```

xfe - lightweight file manager for X11
```


$ sudo apt-get install xfe```

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libfox1.4
Recommended packages:
  rpm
The following NEW packages will be installed:
  libfox1.4 xfe
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 1771kB of archives.
After unpacking 5968kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://us.archive.ubuntu.com dapper/universe libfox1.4
1.4.16-2ubuntu3 [954kB]
Get:2 http://us.archive.ubuntu.com dapper/universe xfe 0.84-4 [816kB]
Fetched 1771kB in 31s (56.0kB/s)
Selecting previously deselected package libfox1.4.
(Reading database ... 32297 files and directories currently installed.)
Unpacking libfox1.4 (from .../libfox1.4_1.4.16-2ubuntu3_amd64.deb) ...
Selecting previously deselected package xfe.
Unpacking xfe (from .../archives/xfe_0.84-4_amd64.deb) ...

Setting up libfox1.4 (1.4.16-2ubuntu3) ...

Setting up xfe (0.84-4) ...
```


$ man equery
No manual entry for equery
$ which equery
No printout


TIA


B.R.
satimis

---

### Post by patrick295767 on 2006-11-10
> **satimis said:**
> Hi folks,

ubuntu-6.06.1-LAMP-server-amd64

Please advise which package-tool provides "equery" command


$ sudo apt-cache search equery```

xfe - lightweight file manager for X11
```


$ sudo apt-get install xfe```

Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libfox1.4
Recommended packages:
  rpm
The following NEW packages will be installed:
  libfox1.4 xfe
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 1771kB of archives.
After unpacking 5968kB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://us.archive.ubuntu.com dapper/universe libfox1.4
1.4.16-2ubuntu3 [954kB]
Get:2 http://us.archive.ubuntu.com dapper/universe xfe 0.84-4 [816kB]
Fetched 1771kB in 31s (56.0kB/s)
Selecting previously deselected package libfox1.4.
(Reading database ... 32297 files and directories currently installed.)
Unpacking libfox1.4 (from .../libfox1.4_1.4.16-2ubuntu3_amd64.deb) ...
Selecting previously deselected package xfe.
Unpacking xfe (from .../archives/xfe_0.84-4_amd64.deb) ...

Setting up libfox1.4 (1.4.16-2ubuntu3) ...

Setting up xfe (0.84-4) ...
```


$ man equery
No manual entry for equery
$ which equery
No printout


TIA


B.R.
satimis

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
packages that contain files named like this
packages that contain files or directories named like this
packages that contain files or directories whose names contain the keyword
all files in this package 

I entered it in but prob with Internet...
  
you have more info ab. this command? u could find a man?

---

### Post by satimis on 2006-11-10
Hi patrick295767,

Tks for your response and Link.

I found this small command which is in Gentoo toolkits.  On Ubuntu I found another package, xfe, which also offers "equery".  But it is not the same command as that in Gentoo.


B.R.
satimis

---

