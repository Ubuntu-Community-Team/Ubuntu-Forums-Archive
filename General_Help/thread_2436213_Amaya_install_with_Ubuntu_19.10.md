---
title: "Amaya install with Ubuntu 19.10"
date: 2020-02-02
forum: General Help
---

### Post by vmux on 2020-02-02
Does anyone know how to install Amaya on Ubuntu 19.10?

When I try to install I get the following dependency errors:

vmux@VMux-Osiris-14:~/Downloads$ sudo dpkg -i amaya_11.4.4-1_amd64.deb 
Selecting previously unselected package amaya.
(Reading database ... 211972 files and directories currently installed.)
Preparing to unpack amaya_11.4.4-1_amd64.deb ...
Unpacking amaya (11.4.4-1) ...
dpkg: dependency problems prevent configuration of amaya:
 amaya depends on libraptor1 (>= 1.4.16); however:
  Package libraptor1 is not installed.
 amaya depends on libssl0.9.8 (>= 0.9.8f-5); however:
  Package libssl0.9.8 is not installed.

I tried installing libraptor1 but I get this error:
vmux@VMux-Osiris-14:~/Downloads$ sudo apt-get install libraptor1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libraptor1 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

I don't know what else to try.

Thanks

---

### Post by CelticWarrior on 2020-02-02
Probably not possible... That software hasn't seen an update in years, many years.

---

### Post by vmux on 2020-02-02
Is there any WYSIWYG html editors for Ubuntu 19.10? I've tried installing google-webdesigner, Amaya, and Kompozor but they all failed with 19.10.

---

### Post by CelticWarrior on 2020-02-02
Google-Webdesigner installs and works fine in 19.10.

---

### Post by vmux on 2020-02-02
That's interesting. When I tried installing it I saw it under Add-Ons but didn't see where to run it from.

---

### Post by CelticWarrior on 2020-02-02
It runs like any other app. Just tested so I know it's working. Just download the .deb file and install like any other software.

---

### Post by vmux on 2020-02-03
When I install it I don't see it in the apps list. Does this install look like yours?

vmux@VMux-Osiris-14:~/Downloads$ sudo dpkg -i google-webdesigner_current_amd64.deb
[sudo] password for vmux:
(Reading database ... 212059 files and directories currently installed.)
Preparing to unpack google-webdesigner_current_amd64.deb ...
Unpacking google-webdesigner (5.2.0.0-1) over (5.2.0.0-1) ...
Setting up google-webdesigner (5.2.0.0-1) ...
Processing triggers for bamfdaemon (0.5.3+18.04.20180207.2-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu1) ...
Processing triggers for mime-support (3.63ubuntu1) ...

---

### Post by CelticWarrior on 2020-02-03
It should be fine. The only difference is I installed it with Ubuntu software, the "app store" but that should have no impact on the end result.

---

### Post by vmux on 2020-02-03
Unfortunately mine doesn't appear in installed apps. Also if I search for Google Web Designer it doesn't appear in the "app store".

---

### Post by CelticWarrior on 2020-02-03
> **vmux said:**
> Unfortunately mine doesn't appear in installed apps. 

You have something wrong in your system.



> Also if I search for Google Web Designer it doesn't appear in the "app store".

Of course not! It is NOT in the Ubuntu repositories. But any .deb packaged software can be installed with the same "app store" which is actually what it opens with when double-clicking the .deb.

---

### Post by vmux on 2020-02-03
Yeah I guess there is something wrong with my system but other programs install correctly. With google-webdesigner I see the application in the Add-ons section of the applications. I appreciate all the help you gave me.

---

### Post by Shay123 on 2021-01-06
Yes but the Ubuntu software installer doesn't like the amaya packages provided by the website - says it does not know how to handle them. Further to this, if you use the .deb installer package it says it can not configure the dependencies and you are left with a non-launching icon. I see messages about the non launch on the Amaya website but they do not work either. Ubuntu will soon be redundant as I will be moving my long standing affiliation but I would like to get my website software functioning now and later on a new linux system.
So, potentially very useful wysiwyg editor made redundant by poor instructions on installation and there are not many to choose from.

---

### Post by ActionParsnip on 2021-01-06
[https://thelinuxcode.com/free-wysiwyg-html-editor/](https://thelinuxcode.com/free-wysiwyg-html-editor/)

---

### Post by ActionParsnip on 2021-01-06
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Ubuntu 19.10 is also EOL (end of life) as of July last year. There will be no packages for it. I suggest you upgrade to Focal (Ubuntu 20.04) for continued support

---

### Post by coffeecat on 2021-01-06
Back to sleep, ancient thread.

Closed.

---

