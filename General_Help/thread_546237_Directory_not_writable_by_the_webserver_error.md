---
title: "Directory not writable by the webserver error"
date: 2007-09-08
forum: General Help
---

### Post by prickly on 2007-09-08
I have been following this guide: [http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu](http://www.mediawiki.org/wiki/Manual:Running_MediaWiki_on_Ubuntu) to install MediaWiki on Ubuntu Server 6.06

The problems that I have are that when i try to upload a file i get the following error:

The upload directory (/var/www/wiki/images) is not writable by the webserver. 

Can someone pls advise me of the correct command line to enable the webserver to write to this directory.

Many thanks

---

### Post by chalex on 2007-09-08
Something like 'chown -R apache: /var/www/wiki/images'

---

### Post by prickly on 2007-09-08
Thanks very much - i will give that a try! :)

---

### Post by prickly on 2007-09-10
I get the following error:

chown: 'apache:' :cannot get the login group of an numeric UID.

Any assistance is much appreciated.

---

### Post by Alex1770 on 2007-09-10
I'm slightly guessing, but the command might be more like ```
chown www-data:www-data /var/www/wiki/images
```.

---

### Post by Alex1770 on 2007-09-10
Or maybe chown -R [+same] if there are other subdirectories.

---

### Post by prickly on 2007-09-10
Thanks - i will give it another go :)

---

### Post by prickly on 2007-09-11
Thanks very much for the solution Alex - very much appreciated! :)

---

