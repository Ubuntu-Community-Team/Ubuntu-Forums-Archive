---
title: "sitecopy sees only first site from ~/.sitecopyrc"
date: 2007-04-22
forum: General Help
---

### Post by ifokkema on 2007-04-22
Hi guys,

For all those fellow Feisty users having problems with sitecopy as it magically only reads out the first site from the config file at ~/.sitecopyrc:

Bug was reported [here]("https://bugs.launchpad.net/ubuntu/+source/sitecopy/+bug/90121"), my solution was to [download the Edgy version]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fs%2Fsitecopy%2Fsitecopy_0.16.3-1_i386.deb&md5sum=ae7c5c6d4b5b46bbd997ed44654a4914&arch=i386&type=main") and install it by typing:
```
sudo dpkg -i sitecopy_0.16.3-1_i386.deb
```

Ivo

---

### Post by rossarn on 2007-07-14
I had a problem with the above Edgy package depending on libgnutls12 which isn't in the default Feisty packages.

I found it easier to use the debian package, which doesn't have this dependency:

[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fs%2Fsitecopy%2Fsitecopy_0.16.3-5_i386.deb&md5sum=34fe1e53121a27283aab0a90409147fb&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fs%2Fsitecopy%2Fsitecopy_0.16.3-5_i386.deb&md5sum=34fe1e53121a27283aab0a90409147fb&arch=i386&type=main)

---

