---
title: "Broken packages Libreoffice"
date: 2014-08-19
forum: General Help
---

### Post by Canaryguy on 2014-08-19
Hello,

I installed Libreoffice using ppa:libreoffice/libreoffice-4-3. 
Later I removed this repository and I uninstalled Libreoffice 4.3.
Now I have broken packages in Synaptic that are not possible to remove and in the Terminal I get errors. Can I do something to fix them? I attached some pictures.

---

### Post by claracc on 2014-08-19
You van try to run in a xterm the following command:

```
sudo apt-get install -f
```

To try to repair broken packages. Please post the output of the command.

---

### Post by Canaryguy on 2014-08-19
> **claracc said:**
> You van try to run in a xterm the following command:

```
sudo apt-get install -f
```

To try to repair broken packages. Please post the output of the command.

This is what I get:

adminpc@adminpc-HP-Pavilion-dv6-Notebook-PC:~$ sudo apt-get install -f
[sudo] password for adminpc: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libreoffice-base
0 upgraded, 0 newly installed, 1 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 6.595 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 265101 files and directories currently installed.)
Removing libreoffice-base (1:4.3.0-0ubuntu1~trusty1) ...
No diversion 'diversion of /usr/lib/libreoffice/share/basic/dialog.xlc to /usr/lib/libreoffice/share/basic/dialog.xlc.noaccess by libreoffice-base', none removed.
No diversion 'diversion of /usr/lib/libreoffice/share/basic/script.xlc to /usr/lib/libreoffice/share/basic/script.xlc.noaccess by libreoffice-base', none removed.
/var/lib/dpkg/info/libreoffice-base.postrm: 28: /var/lib/dpkg/info/libreoffice-base.postrm: Syntax error: end of file unexpected (expecting "fi")
dpkg: error processing package libreoffice-base (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libreoffice-base
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by slickymaster on 2014-08-19
You can try to remove it manually by running these commands:```
mv /var/lib/dpkg/info/libreoffice-base.* /tmp/
dpkg --remove --force-remove-reinstreq libreoffice-base
```

---

### Post by claracc on 2014-08-19
Please, see this link: [https://www.kubuntuforums.net/showthread.php?66147-How-to-get-rid-of-a-broken-package-libreoffice-base](https://www.kubuntuforums.net/showthread.php?66147-How-to-get-rid-of-a-broken-package-libreoffice-base) it seems to have the same problem.

---

### Post by Canaryguy on 2014-08-19
Thanks slickymaster. Problem solved.

---

### Post by slickymaster on 2014-08-19
You're welcome. Glad you got it fixed.

---

### Post by michaelg81 on 2014-10-20
This solved my issues as well!

---

