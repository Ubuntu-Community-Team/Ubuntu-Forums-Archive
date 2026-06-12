---
title: "apache .sh execu"
date: 2019-04-30
forum: General Help
---

### Post by aminbaik on 2019-04-30
Hello,
I have a php file that is excue a .sh command:
<?php
  echo exec('/var/www/html/disable.sh');
?>

the .sh file command is:
sudo  cp /var/www/html/1.cfg /var/www/html/2.cfg

when I run it from ssh from root user account using 
php /var/www/html/disable.php the /sh work fine 
when I runt it from browser is not working !
so what I have to do ?
I am using lts16.4
thanks.

---

### Post by Holger_Gehrke on 2019-04-30
Why use exec() when php has a perfectly usable [copy()-function]("https://www.php.net/manual/en/book.filesystem.php") in the filesystem-extension that AFAIK is part of the core of PHP ? exec is a somewhat risky operation and is disabled on a lot of production servers. Better not to rely on it.

Beyond that: /var/www/html is owned by root, PHP runs as the web-server (www-data). So it can't write there (there are good, security-related reasons for that; the web-server is basically a program under outside - potentially hostile - control; allowing it to write in places where code it executes is stored is just asking for trouble). 'sudo' is not a solution to this problem since it's meant for interactive use (yes, it's possible to hack something up; no that's **not** a good idea). If those files are used/needed by some web-application you have some degree of familiarity with and control over, then you could create a directory with ownership and permission set in such a  way that php **can** write there (owner www-data, permission 744 or  something like that ...) and make that web-app read those files from there.

Holger

---

### Post by aminbaik on 2019-05-28
hello,
the .sh file i post it is a simple it' will do more than copy,.
the owner of files and folder is www-data.
any suggest ?
thanks.

---

### Post by SeijiSensei on 2019-05-28
What do you see in /var/log/apache2/error.log? You should always consult the logs as the first step in troubleshooting.

---

