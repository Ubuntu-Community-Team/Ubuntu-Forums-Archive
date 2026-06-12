---
title: "Ubuntu Repo -  su - apt-mirror -c apt-mirror errors"
date: 2015-08-13
forum: General Help
---

### Post by devtaz on 2015-08-13
I am trying to stand up an internal repo server, I have been following the documents online, but I am running into permission denied errors as noted below.. I have included the start... I have the mirror done, ~150gb of data, it appears to be trying to build the links.  it's running as root, do I need to modify directory permissions?

root@ubuntu-repo:~# su - apt-mirror -c apt-mirror
Downloading 270 index files using 20 threads...
Begin time: Thu Aug 13 09:54:48 2015
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]...
End time: Thu Aug 13 09:54:59 2015

Processing tranlation indexes: [TTTTT]

Downloading 738 translation files using 20 threads...
Begin time: Thu Aug 13 09:54:59 2015
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]...
End time: Thu Aug 13 09:55:17 2015

Processing indexes: [SSSSsh: 1: cannot create archive.ubuntu.com/ubuntu//dists/trusty-proposed/main/source/Sources: Permission denied
sh: 1: cannot create archive.ubuntu.com/ubuntu//dists/trusty-proposed/restricted/source/Sources: Permission denied
sh: 1: cannot create archive.ubuntu.com/ubuntu//dists/trusty-proposed/universe/source/Sources: Permission denied
sh: 1: cannot create archive.ubuntu.com/ubuntu//dists/trusty-proposed/multiverse/source/Sources: Permission denied
Ssh: 1: cannot create archive.ubuntu.com/ubuntu//dists/trusty-backports/main/source/Sources: Permission denied
sh: 1: cannot create archive.ubuntu.com/ubuntu//dists/trusty-backports/restricted/source/Sources: Permission denied

then I get the following further down;

apt-mirror: can't copy /var/spool/apt-mirror/skel/archive.ubuntu.com/ubuntu/dists/trusty-proposed/universe/i18n/Translation-zh_TW to /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/trusty-proposed/universe/i18n/Translation-zh_TW at /usr/bin/apt-mirror line 803.
0 bytes in 0 files and 0 directories can be freed.
Run /var/spool/apt-mirror/var/clean.sh for this purpose.

any help would be appreciated.

---

