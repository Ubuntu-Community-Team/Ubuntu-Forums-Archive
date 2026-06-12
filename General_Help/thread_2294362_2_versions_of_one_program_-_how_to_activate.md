---
title: "2 versions of one program - how to activate"
date: 2015-09-10
forum: General Help
---

### Post by Kevin McCready on 2015-09-10
The version of libreoffice which came with my ubuntu was 4.?
When I change footnotes to endnotes they didn't display.
So I downloaded and installed libreoffice version 5 via a tar.gz file and followed the readme instructions via
sudo dpkg -i *.deb
So apparently now I have two version installed side by side. But how do I use version 5?

---

### Post by HermanAB on 2015-09-11
The simplest way? Right click on the desktop and make a launcher.

---

### Post by tgalati4 on 2015-09-11
Open a terminal:

```
which libreoffice
```

The default installation in located in /usr/bin.

> tgalati4@Mint17 ~/Desktop $ which libreoffice
/usr/bin/libreoffice


---

### Post by Kevin McCready on 2015-09-11
making a launcher didn't work. It launches 4.4.3.2 which I don't want. Somewhere on my system there should be a version 5.0.1 if the commands  I executed above worked (and they didn't give me any error). 

Using the which command was fun but didn't help.

It must be a common problem to have two versions side by side on a system and be able to chose which one to run? But how?

---

### Post by tgalati4 on 2015-09-12
What is the output of:

```
whereis libreoffice
```

If you examine the contents of /usr/bin/libreoffice, you will find that it is a symbolic link that points to a script.  One which you can modify to get your newer version of libreoffice to run.

> tgalati4@Mint17 /usr/bin $ ls -la libreoffice
lrwxrwxrwx 1 root root 34 Apr 23 15:56 libreoffice -> ../lib/libreoffice/program/soffice
tgalati4@Mint17 /usr/bin $ more ../lib/libreoffice/program/soffice
#!/bin/sh
#
# This file is part of the LibreOffice project.
#
# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
.
.
.


---

### Post by Kevin McCready on 2015-09-12
$ which libreoffice
/usr/bin/libreoffice
cd /usr/bin
/usr/bin $ ls -la libreoffice
lrwxrwxrwx 1 root root 34 Sep  4 17:10 libreoffice -> ../lib/libreoffice/program/soffice
k@k-eM350 /usr/bin $ more ../lib/libreoffice/program/soffice
#!/bin/sh
#
# This file is part of the LibreOffice project.


but it would be nice to be able to choose which version I run from time to time.

---

