---
title: "php on apache2"
date: 2004-11-28
forum: General Help
---

### Post by Razvan on 2004-11-28
sorry!!! DONTMIND! I WORKED IT OUT!

hi all,

i want to set up a small php-server.

installed:

apache2
apache2-common
apache2-mpm-prefork
libapache2-mod-auth-mysql
libapache2-mod-php4
apache-common
apche-utils
php4
and all the mysqlstuff (mysql works)

when i try to acces any php file via firefox, it just wants to download it like a ordinary file  :twisted: 

do i have to install anything else?
i made a symlink from /etc/apache2/mods-available/php4.conf to .../mods-enabled/php4.conf
and from                                                                               php4.load to .../mods-enabled/php4.load

do i need any other modules?

any other ideas?

thanks, Martin

---

### Post by jiyuu0 on 2004-11-28
[http://kitech.com.my/ubuntu/4.10/index.html#apachehttpserver](http://kitech.com.my/ubuntu/4.10/index.html#apachehttpserver)

---

### Post by kevcool on 2005-10-04
Well, what did you do to resolve it?  I've got the same problem.

Both apache and apache2 won't execute a php file on the server so the client wants to download it as a normal file.

(I'm using Hoary BTW)

Thanks in advance.

---

### Post by fmasi on 2005-10-05
It will be nice if you told us how did you fix it becouse i have exacly the same issue. Firefor whats to download all php files. Snifff

---

### Post by oxEz on 2005-10-09
I just fixed it on my computer, you need to install libapache2-mod-php5

```
sudo apt-get install libapache2-mod-php5
```

---

### Post by SuperMike on 2005-11-25
[QUOTE=oxEz]I just fixed it on my computer, you need to install libapache2-mod-php5

```
sudo apt-get install libapache2-mod-php5
```[/QUOTE]

I think I'm seeing a pattern of an undocumented Ubuntu Breezy bug in PHP5 and PHP4 installs with the libapache2-mod-php4 or libapache2-mod-php5. If you uninstall and reinstall multiple times, you'll find that it just sort of works if you repeat the process several times. I had to repeat the same exact process like 5 times on my PC before it just worked. And when you uninstall PHP, it will warn you that libapache2-mod-php(x) didn't get installed in the first place, so it can't remove it.

My running theory here is that either there's a bug in the Canonical web farm with some of the mirror servers we're hitting. I cannot figure out any other reason why the libapache2-mod-php(x) would install one time and not another.

And if you do a search on ubuntuforums.org, you'll find that a lot of people are having this issue.

I finally got my PHP4 to work in Breezy. A couple days ago, I also had my PHP5 working too. So it *can* be done. Just keep playing with Synaptic and the install, trying different ways to install it, or install just what you need first and add other extra PHP items you need as you go. You'll find if you keep fighting with it for like 4 hours, it finally just *works*, somehow.

---

