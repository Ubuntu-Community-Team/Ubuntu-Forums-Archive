---
title: "[SOLVED] Force Remove Package?"
date: 2008-04-12
forum: General Help
---

### Post by myusername on 2008-04-12
i need help force removing this broken package epiphany-browser-data ...epiphany is gone but this package is broken and won't let me uninstall/reinstall it or any other package...i have tried everything throught synaptic ant the terminal but it just won't go away herew is what it says

from synaptic: An error occured 
The following details are provided
:E: epiphany-browser-data: subprocess post-removal script returned error exit status 2

froim cli
The following packages will be REMOVED:
  epiphany-browser-data
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 14.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 78772 files and directories currently installed.)
Removing epiphany-browser-data ...
/usr/share/icons/HighContrastLargePrint is not a directory
dpkg: error processing epiphany-browser-data (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 epiphany-browser-data
E: Sub-process /usr/bin/dpkg returned an error code (1)


can anyone help?

---

### Post by sekinto on 2008-04-13
Try "dpkg -P <your package>".

---

### Post by myusername on 2008-04-13
didnt work...


andrew@Xubuntu:~$ sudo dpkg -P epiphany-browser-data
[sudo] password for andrew:
(Reading database ... 78772 files and directories currently installed.)
Removing epiphany-browser-data ...
/usr/share/icons/HighContrastLargePrint is not a directory
dpkg: error processing epiphany-browser-data (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 epiphany-browser-data

---

### Post by sekinto on 2008-04-13
I had the same problem with removing MoBlock, I had do delete a startup script for it in my /etc/init.d directory. But I don't think Epiphany has any startup scripts by default, so I doubt that is the case here. Have you tried making the directory it is complaining about?

---

### Post by myusername on 2008-04-13
it worked!

---

