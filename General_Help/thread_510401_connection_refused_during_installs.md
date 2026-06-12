---
title: "connection refused during installs"
date: 2007-07-26
forum: General Help
---

### Post by FreeSoul on 2007-07-26
Hello All,

    I've tried the following:

sudo apt-get install alsamixergui
and
sudo apt-get install k3b

I've received connection refused errors (I'm in Germany if that matters) both from the gui and the stated command line. I was able to install all the other alsa components needed though.

Here is a sample message after selecting "y" from the command line for k3b:

> After unpacking 12.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main libflac++5c2 1.1.2-5ubuntu2
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main libk3b2 1.0-0ubuntu2
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main k3b 1.0-0ubuntu2
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/flac/libflac++5c2_1.1.2-5ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/flac/libflac++5c2_1.1.2-5ubuntu2_i386.deb)  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/k/k3b/libk3b2_1.0-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/k/k3b/libk3b2_1.0-0ubuntu2_i386.deb)  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0-0ubuntu2_i386.deb)  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


And for alsamixergui:

> After unpacking 1016kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main libfltk1.1 1.1.7-2
  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/fltk1.1/libfltk1.1_1.1.7-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/fltk1.1/libfltk1.1_1.1.7-2_i386.deb)  Could not connect to au.archive.ubuntu.com:80 (211.29.132.173). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


Any ideas?

Thanks,
FreeSoul

---

### Post by davidjmayo on 2007-07-26
There are problems with the au repos

see here for info & solutions
[http://ubuntuforums.org/showthread.php?t=508981](http://ubuntuforums.org/showthread.php?t=508981)

---

