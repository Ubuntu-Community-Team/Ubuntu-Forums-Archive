---
title: "accidentally deleted package conf file - but how do i get it back?"
date: 2007-05-31
forum: General Help
---

### Post by hantzis on 2007-05-31
accidentally deleted php5.conf, php5.load in libapache2-mod-php5 apt-get package. 

I have sudo apt-get remove libapache2-mod-php5
then sudo apt-get install libapache2-mod-php5

But the php5.conf and php5.load files don't re-create. 

This seems to happen with any package. If a conf file is deleted, removing and reinstalling using apt-get will not re-create the file(s). 

Any ideas?

---

### Post by pbw on 2007-05-31
They should. try apt-get remove --purge, If that doesnt work for you i don't mind uploading the two default files. Just lemme know.

-- pbw

---

### Post by hantzis on 2007-06-03
> **pbw said:**
> They should. try apt-get remove --purge, If that doesnt work for you i don't mind uploading the two default files. Just lemme know.

-- pbw

Yes! That did it. Thanks!

---

