---
title: "MySQL support unavailable?"
date: 2007-02-12
forum: General Help
---

### Post by cocotu on 2007-02-12
I was not sure where to post this.  I have Ubuntu 6.06 and installed Apache, MySQL, PHP in order to install Joomla! at my local machine for practice purposes.  I get an error saying: MySQL support unavailable.  I was told that I needed to compile again PHP to support MySQL databases.  I saw a command "--with-mysql=DIR", but not sure if I have to do this if I did NOT install Apache, MySQL, PHP from source.  I used Synaptic to install all these 3 items.  Any ideas to what I need to do in this case?

Thanks

---

### Post by seppo on 2007-02-12
there is need to compile PHP from scratch. Just install the phpmysql module:

sudo apt-get install php4-mysql

If you use PHP5 , replace the 4 with a 5 ;-)

---

### Post by cocotu on 2007-02-12
Thanks seppo! I had php5-mysql installed, but I had to re-install it and everything worked fine.  It seems that the order of installation attects everything.  I was looking around and found that the order of installation should be:
1. Apache
2. MySQL
3. PHP

Thanks!!

---

### Post by seppo on 2007-02-13
> **cocotu said:**
> Thanks seppo! I had php5-mysql installed, but I had to re-install it and everything worked fine.  It seems that the order of installation attects everything.  I was looking around and found that the order of installation should be:
1. Apache
2. MySQL
3. PHP

Thanks!!

Glad to hear it worked! :)

---

