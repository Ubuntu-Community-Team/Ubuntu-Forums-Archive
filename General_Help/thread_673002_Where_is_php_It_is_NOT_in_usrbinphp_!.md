---
title: "Where is php? It is NOT in /usr/bin/php !"
date: 2008-01-20
forum: General Help
---

### Post by technoboi on 2008-01-20
I am using Ubuntu 7.10. I am trying out an installation on the desktop version before trying it out on my 'alt' installation which is more precious as it has MythTV set up on it and that took a long time to commission.
I can't install freepbx because php is not located in /usr/bin/php. So where is the PHP binary?
I have looked at countless postings, via Google, asking this very same question,  but no one, it seems, has yet come up with the right answer. Yes I have done 'whereis' etc. - it just doesn't help at all. PHP5 is installed - it works! So where is php hidden on Ubuntu?  Further WHY is it installed somewhere non-standard?  Ghrrr this is driving me crazy!
Please can anyone help?

---

### Post by Miademora on 2008-01-20
try:

whereis php5

its most likely in /usr/bin/php5

---

### Post by technoboi on 2008-01-20
> **Miademora said:**
> try:

whereis php5

its most likely in /usr/bin/php5
Yes, I have already tried that of course. Thanks anyway. If you have Ubuntu 7.10 just try finding it, it isn't easy - well I didn't  find it so anyway.  :-(

---

### Post by p_quarles on 2008-01-20
PHP is many different packages. If you have the Apache 2 module for PHP5, the executable is Apache itself. If you install the command line interpreter (package name is "php5-cgi") you'll get a standalone executable in /usr/bin.

If you say what you're trying to do you can probably get better help.

---

### Post by heindsight on 2008-01-20
make sure that you have the php5-cli package installed

---

### Post by dagnabit dang doohickey on 2008-01-20
Gutsy php5 file locations:
[php5-cli]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=php5-cli&version=gutsy&arch=i386")
[php5-cgi]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=php5-cgi&version=gutsy&arch=i386")
[libapache2-mod-php5]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=libapache2-mod-php5&version=gutsy&arch=i386")

---

### Post by backwardselvis on 2008-01-21
Try the following command.

```
# sudo find / -name "php*" 
```

-elvis

---

