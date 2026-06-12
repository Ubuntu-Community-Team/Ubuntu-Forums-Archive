---
title: "Invalid command 'php_flag'"
date: 2007-05-22
forum: General Help
---

### Post by Reskiebak on 2007-05-22
Hi, maybe someone can help me here.

I have an ubuntu box. I used vhcs2 for site management.
Everything went fine will I installed a wiki (mediawiki) the latest version needed php5.. so
I used the aptitude to get php5. But my vhc2 stopped working, I thought because of a missing php-mcrypt package. SO I tried to install it but it messed up with the php and apache.
So I tried to reinstall php 5 and I got this when I reload apache:


Forcing reload of web server (apache2)...Syntax error on line 22 of /etc/apache2/sites-available/vhcs2.conf:
Invalid command 'php_flag', perhaps misspelled or defined by a module not included in the server configuration
failed!

It didnt worked with php5, tried php4 with the same result. Apache seems to not know the php_flag command.
Any help Here?
Thanks.

---

### Post by benmoreassynt on 2007-05-22
I reckon you might be better asking the question on the php mailing list ([http://www.php.net/mailing-lists.php](http://www.php.net/mailing-lists.php)), and also finding out about the vhcs2.conf file and how to configure it. It sounds like a problem with the vhc2. Can you try a clean install of vhc2 instead?

---

