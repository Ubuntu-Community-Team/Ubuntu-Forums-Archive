---
title: "A good MySQL front-end?"
date: 2005-06-08
forum: General Help
---

### Post by word_virus on 2005-06-08
Hey, folks!

Anyone know of a good frontend for MySQL, similar to SQL-Front on Windows? I did a little googlin' but couldn't really find what I was after.

Thanks!

---

### Post by wellery on 2005-06-08
[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php).

It's web based though and uses php.

---

### Post by word_virus on 2005-06-09
[QUOTE=wellery][http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php).

It's web based though and uses php.[/QUOTE]

I have used phpmyadmin before and it's a good program, but like you say it's web based and requires php.  SQL-Front's nice cause it's stand-alone.

Thanks, though.  Guess I'll just have to keep lookin'...

---

### Post by djg on 2005-06-10
[QUOTE=word_virus]Hey, folks!

Anyone know of a good frontend for MySQL, similar to SQL-Front on Windows? I did a little googlin' but couldn't really find what I was after.

Thanks![/QUOTE]
 MySQLcc is worth a look.  It's the previous official release from MySQL AB.

---

### Post by dmalopsy on 2005-06-10
Yep MysqlCC is the your best bet. Its one of the best that I have used for Linux, it also comes in a Windows version too. i think if you apt-get install mysqlcc will install it for you.

---

### Post by C03N on 2005-06-10
After the install, do the following to create a MySQLCC shortcut in Applications >> System Tools:

sudo vi /usr/share/applications/MySQLCC.desktop

and insert the following text:

[Desktop Entry]
Name=MySQLCC
Comment=MySQLCC
Exec=mysqlcc
Icon=/usr/share/pixmaps/mysqlcc.xpm
Terminal=false
Type=Application
Categories=Application;System;

The **Unofficial Ubuntu 5.04 Starter Guide** is a very good pre-forum reference and can be accessed via the following link: [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by word_virus on 2005-06-10
MySQLcc is just perfect! Thanks for the tip, everybody!

---

