---
title: "apt-get install pptp-linux needs cd???"
date: 2005-03-31
forum: General Help
---

### Post by corefile on 2005-03-31
apt-get install pptp-linux

Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  pptp-linux
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/93.9kB of archives.
After unpacking 217kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050310)'
in the drive '/cdrom/' and press enter

Why do I need to put in the CD? I don't have the dang thing any more, and whats the point anyway it should download what ever it needs. This seems broke to me.

---

### Post by fdoving on 2005-03-31
take a look at the /etc/apt/sources.list file.. uncomment the "deb http://archive..." lines
and add # in front of "deb cdrom... " lines.

then do apt-get update;apt-get isntall pptp-linux


Good luck.

---

### Post by corefile on 2005-03-31
perfect that did it, I already had the archive part uncomented but did not have cdrom commented out, did that and it installed with no problem. Thanks.

---

