---
title: "PHP Apache problems."
date: 2007-09-29
forum: General Help
---

### Post by arckeda on 2007-09-29
Hello, I recently installed apache2 and it works like a charm, I used apt-get to install php5, yet for some reason when I try to visit a php page, it asks me to download the file, it seems that php5 is not working, what should I do?  Thank you.

     -ARCKEDA

---

### Post by Malibu Illusion on 2007-09-29
```
sudo aptitude install libapache2-mod-php5
sudo apache2ctl restart
```

Apache doesn't just magically start working because you have PHP on your system; you have to provide it with a specific module to make using the engine possible.

---

### Post by arckeda on 2007-09-29
I already have that installed.

---

### Post by arckeda on 2007-09-29
Checking aptitude shows that php5, php5-common, apache2, and apache2.2-common are all installed and working.

---

### Post by arckeda on 2007-09-29
Bump

---

### Post by arckeda on 2007-09-30
Bump!

---

### Post by Malibu Illusion on 2007-09-30
> **arckeda said:**
> Checking aptitude shows that php5, php5-common, apache2, and apache2.2-common are all installed and working.

So where is libapache2-mod-php5?

What is the output of:

```
ls -l /usr/lib/apache2/modules/ | grep php
```

What about:

```
ls -l /etc/apache2/mods-available/ | grep php
```

and:

```
ls -l /etc/apache2/mods-enabled/ | grep php
```

---

### Post by arckeda on 2007-09-30
arckeda@NEXUS:~$ ls -l /usr/lib/apache2/modules/ | grep php
-rw-r--r-- 1 root root 5614424 2007-07-17 13:15 libphp5.so
arckeda@NEXUS:~$ ls -l /etc/apache2/mods-available/ | grep php
arckeda@NEXUS:~$ ls -l /etc/apache2/mods-enabled/ | grep php
arckeda@NEXUS:~$

So I need to enable it?  How would I go about doing that?

libapache2-mod-php5 appears to be installed.

---

### Post by arckeda on 2007-10-01
Bump.

---

### Post by arckeda on 2007-10-01
Bump!  AGAIN!

---

### Post by arckeda on 2007-10-02
Bump!

---

### Post by Malibu Illusion on 2007-10-04
```
gksudo gedit /etc/apache2/mods-enabled/php5.conf
```

(or whatever your favorite text editor is.)

Into that file, insert:

```
<IfModule mod_php5.c>
AddType application/x-httpd-php .php .phtml .php3
AddType application/x-httpd-php-source .phps
</IfModule>
```

Save the file.  Exit the editor.

Now:

```
gksudo gedit /etc/apache2/mods-enabled/php5.load
```

And into that...

```
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so
```

Save the file, exit the editor.

Now:

```
sudo apache2ctl restart
```

PHP should now work.

---

### Post by arckeda on 2007-10-04
Bump!

---

