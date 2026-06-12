---
title: "Problems with Lubuntu Software Center"
date: 2016-02-05
forum: General Help
---

### Post by krzysztofzych on 2016-02-05
I have some problems with *Lubuntu Software Center*. I launch it and everything seems okay, but when i look for programs i don't see most of the programs (*Libre Office, VLC Media Player* for example). What to do?

---

### Post by vasa1 on 2016-02-05
Have you enabled "universe" in your software sources?

I see both.

---

### Post by ajgreeny on 2016-02-05
have you refreshed the repos in software-center?  Until you do that it will not see many packages.

---

### Post by yoshii on 2016-02-05
This is not directly related, but if you are interested, Ubuntu Software Center can also be run within Lubuntu.  You just have to install it first.  Unfortunately, I can't remember which command I used to install it.  Maybe somebody else knows.

---

### Post by vasa1 on 2016-02-05
> **yoshi2 said:**
> This is not directly related, but if you are interested, Ubuntu Software Center can also be run within Lubuntu.  You just have to install it first.  Unfortunately, I can't remember which command I used to install it.  Maybe somebody else knows.
Before doing so, please check what else will be pulled in. Then decide. 

```
The following NEW packages will be installed:
  apt-xapian-index gir1.2-gmenu-3.0 gir1.2-gstreamer-1.0 libgnome-menu-3-0
  oneconf oneconf-common python-commandnotfound python-crypto python-debtagshw
  python-dirspec python-gdbm python-gi-cairo python-httplib2 python-lxml
  python-oauthlib python-oneconf python-openssl python-pam
  python-piston-mini-client python-serial python-twisted-bin
  python-twisted-core python-twisted-web python-ubuntu-sso-client
  python-xapian python-zope.interface python3-crypto python3-httplib2
  python3-oauthlib python3-oneconf python3-piston-mini-client python3-xdg
  sessioninstaller software-center software-center-aptdaemon-plugins
  ubuntu-sso-client

```I'd strongly advise _***not***_ installing it unless there's a very, very good reason.

---

