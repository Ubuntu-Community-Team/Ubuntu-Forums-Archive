---
title: "Problem on installing xfonts-intl-chinese"
date: 2007-08-18
forum: General Help
---

### Post by satimis on 2007-08-18
Hi folks,


Ubuntu 7.04 lamp server amd64
xfont-intl-chinese


I encountered problem on installing the captioned package which has to be installed on /usr/lib/X11/fonts/misc

/usr/lib/X11 already existed

$ sudo mkdir -R /usr/lib/X11/fonts/misc```

mkdir: invalid option -- R
Try `mkdir --help' for more information.

```

The option -R was not available.  

$ sudo mkdir /usr/lib/X11/fonts/misc
No complaint

$ ls -al /usr/lib/X11/fonts/misc```

total 8
drwxr-xr-x 2 root root 4096 2007-08-18 23:03 .
drwxr-xr-x 3 root root 4096 2007-08-18 23:03 ..

```

$ ls -al /usr/lib/X11/fonts/```

total 12
drwxr-xr-x 3 root root 4096 2007-08-18 23:03 .
drwxr-xr-x 6 root root 4096 2007-08-18 22:46 ..
drwxr-xr-x 2 root root 4096 2007-08-18 23:03 misc

```

$ sudo apt-get install xfonts-intl-chinese```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpoppler1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  xfonts-intl-chinese-big xfonts-cjk emacs-intl-fonts
The following NEW packages will be installed:
  xfonts-intl-chinese
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/5764kB of archives.
After unpacking 6730kB of additional disk space will be used.
Selecting previously deselected package xfonts-intl-chinese.
(Reading database ... 42727 files and directories currently installed.)
Unpacking xfonts-intl-chinese (from .../xfonts-intl-chinese_1.2.1-6ubuntu1_all.deb) ...
Setting up xfonts-intl-chinese (1.2.1-6ubuntu1) ...

```

The strange thing happened

$ ls -al /usr/lib/X11/fonts/```

total 8
drwxr-xr-x 2 root root 4096 2007-08-18 23:08 .
drwxr-xr-x 6 root root 4096 2007-08-18 22:46 ..

```
The directory "misc" disappeared/removed.  How this happens?

Installation went through w/o complaint.  Where the package was installed.

$ sudo apt-get remove xfonts-intl-chinese
Password:```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpoppler1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xfonts-intl-chinese
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 6730kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 42753 files and directories currently installed.)
Removing xfonts-intl-chinese ...
warning: /usr/lib/X11/fonts/misc does not exist or is not a directory

```
Removal went through looking for "/usr/lib/X11/fonts/misc"


I tried several times having the same result.  Please help.  TIA


B.R.
satimis

---

