---
title: "Correct code, please help"
date: 2016-08-21
forum: General Help
---

### Post by dodo125025 on 2016-08-21
I am following an old guide which requires me to install additional software for php. Here is the code:

```
sudo apt-get install graphviz aspell php5-pspell php5-curl php5-gd php5-intl php5-mysql php5-xmlrpc php5-ldap
```

I tried substituting php5 with php7 but I get 

```

E: Unable to locate package php7-pspell
E: Unable to locate package php7-curl
E: Unable to locate package php7-gd
E: Unable to locate package php7-intl
E: Unable to locate package php7-mysql
E: Unable to locate package php7-xmlrpc
E: Unable to locate package php7-ldap

```

Obviously pointing in the wrong place. Can anyone help?

---

### Post by howefield on 2016-08-21
Drop the number.. (or use 7.0 ?)

```
sudo apt-get install graphviz aspell php-pspell php-curl php-gd php-intl php-mysql php-xmlrpc php-ldap
```

eg....

```
hugh@xenial:~$ sudo apt-get install -s graphviz aspell php-pspell php-curl php-gd php-intl php-mysql php-xmlrpc php-ldap
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aspell is already the newest version (0.60.7~20110707-3build1).
aspell set to manually installed.
The following additional packages will be installed:
  libcdt5 libcgraph6 libgvc6 libgvpr2 libpathplan4 libxmlrpc-epi0 php-common php7.0-common php7.0-curl php7.0-gd php7.0-intl php7.0-ldap
  php7.0-mysql php7.0-pspell php7.0-xmlrpc
Suggested packages:
  graphviz-doc
The following NEW packages will be installed
  graphviz libcdt5 libcgraph6 libgvc6 libgvpr2 libpathplan4 libxmlrpc-epi0 php-common php-curl php-gd php-intl php-ldap php-mysql
  php-pspell php-xmlrpc php7.0-common php7.0-curl php7.0-gd php7.0-intl php7.0-ldap php7.0-mysql php7.0-pspell php7.0-xmlrpc
0 to upgrade, 23 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by dodo125025 on 2016-08-21
Thanks friend! :D

---

### Post by howefield on 2016-08-21
Any time, glad you got it.

---

