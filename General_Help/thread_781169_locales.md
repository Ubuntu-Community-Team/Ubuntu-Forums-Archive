---
title: "locales?"
date: 2008-05-04
forum: General Help
---

### Post by nkobel003 on 2008-05-04
I just upgraded from 7.10 to 8.04, and a ton of stuff doesn't work. For starters, when I update/upgrade, I get this error message:
```

mannequin@NAMELESS-UL:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-image-rt
  linux-restricted-modules linux-restricted-modules-generic
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up locales (2.7.9-4) ...
cat: /var/lib/locales/supported.d/ies4linux-2.99.0.1: Is a directory
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 locales
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

My video card drivers also do not work (and they did in 7.10).

Any ideas?

Thanks

---

### Post by karuptdata on 2008-05-04
Is the locales package installed? If it is login to terminal and run 

```
dpkg-reconfigure locales
``` 

and select your language of course and that should straighten out that issue. If you dont have it installed go ahead and run sudo apt-get install locales.

As for your video card, right click on your menu bar and select "edit menus" The menu editor should pop up. On the left hand payne select other, and then in the right column select screens and graphics. Of course then visit Menu->Other->Screens and Graphics and search for your monitor setting from within there. Hope this helps some :) 

Cheers!

Karuptdata

---

### Post by nkobel003 on 2008-05-05
I got the other packages taken care of (via apt-get update/grade), but locales is still giving me trouble. It is not installed, and this is the error message I get when I sudo apt-get install locales
```

mannequin@NAMELESS-UL:~$ sudo apt-get install locales
Reading package lists... Done
Building dependency tree       
Reading state information... Done
locales is already the newest version.
The following packages were automatically installed and are no longer required:
  unixodbc odbcinst1debian1 linux-headers-2.6.24-16-generic
  linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up locales (2.7.9-4) ...
cat: /var/lib/locales/supported.d/ies4linux-2.99.0.1: Is a directory
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 locales
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

Also, none of that worked for my video card. The drivers are installed, but "Screens and Graphics" always crashes (and even prompts me to send an error report). I'm working on a 640 x 480 resolution right now, and it's so frustrating! lol. I'm just gonna reformat I think.

This is a big problem: firefox 3 didn't carry over my bookmarks. How do I recover them?

Thanks

---

