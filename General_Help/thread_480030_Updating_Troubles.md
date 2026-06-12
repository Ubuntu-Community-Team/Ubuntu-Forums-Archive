---
title: "Updating Troubles"
date: 2007-06-20
forum: General Help
---

### Post by Xephrey on 2007-06-20
I am currently running Ubuntu on a little Dell Inspiron 6000 - the version is Feisty Fawn. Whenever I try and update using update manager, it comes up with this error message:

----------------------------------------------------------------------------------
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://mirror.imbrandon.com/ubuntu/dists/feisty-updates/Release.gpg:](http://mirror.imbrandon.com/ubuntu/dists/feisty-updates/Release.gpg:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty/Release.gpg:](http://mirror.imbrandon.com/ubuntu/dists/feisty/Release.gpg:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/Release.gpg:](http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/Release.gpg:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/main/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/restricted/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/universe/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-security/Release.gpg:](http://mirror.imbrandon.com/ubuntu/dists/feisty-security/Release.gpg:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)
[http://mirror.imbrandon.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:](http://mirror.imbrandon.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:) Could not connect to mirror.imbrandon.com:80 (198.247.173.230). - connect (111 Connection refused)

----------------------------------------------------------------------------------

I do have an internet connection on it, I am posting from it - so thats not the issue. 

Any ideas or pointers?


Thanks!

---

### Post by Ziox on 2007-06-21
are you updating from the standard/default repositories?
also, by checking through the browser, it appears that mirror.imbrandon.com is either down or doesn't exist anymore.

---

