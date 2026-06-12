---
title: "letoDMS on quantal"
date: 2013-01-20
forum: General Help
---

### Post by svance1947 on 2013-01-20
I would like to install letoDMS on quantal.  The problem has been outlined by others:  php-letodms-lucene requires zendframework

For some reason, Ubuntu calls it zend-framework.

I've unpacked the .deb package and corrected the spelling, but don't know what to do next.  As you can tell, I'm not a sophisticated user.

---

### Post by raja.genupula on 2013-01-20
If you got the source of it then you can create you own .deb and you can install it.

so rightnow you need the help of packaging.

my friends refer this [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

---

### Post by svance1947 on 2013-01-20
Thanks,

Found an up-date in bug discussion, but it never made it into the repository.

---

### Post by svance1947 on 2013-01-21
Here are the steps I used to get letoDMS running:

Got up-dated php-letodms-lucene from bug listing
[https://bugs.launchpad.net/ubuntu/+source/php-letodms-lucene/+bug/993070](https://bugs.launchpad.net/ubuntu/+source/php-letodms-lucene/+bug/993070)

Installed zend-framework
Installed php-letodms-lucene up-date

Made config files in etc/letodms writeable

Done

---

### Post by raja.genupula on 2013-01-22
thats a great news , now please mark your thread as solved from thread tools.

Thank you.

---

### Post by svance1947 on 2013-01-22
One last mention:

To access the server from the web, change the access rights in
/etc/apache2/sites-enabled for letodms

---

