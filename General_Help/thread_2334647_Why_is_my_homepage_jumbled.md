---
title: "Why is my homepage jumbled?"
date: 2016-08-21
forum: General Help
---

### Post by dodo125025 on 2016-08-21
Trying to set up a linux desktop with apache. Can anyone tell me my localhost is showing a jumble like this? I thin it is pointing in the correct folder/file.

 [ATTACH=CONFIG]270789[/ATTACH]

---

### Post by &amp;KyT$0P# on 2016-08-21
I see that you're using Firefox with some add-ons installed.  To try to rule out browser-end issues, please start Firefox in [Safe mode]("http://kb.mozillazine.org/Safe_Mode") does the problem still occur?

---

### Post by dragonfly41 on 2016-08-21
Starting with basics .. have you followed the setup instructions as here ..

[https://docs.moodle.org/24/en/Installation_Quickstart](https://docs.moodle.org/24/en/Installation_Quickstart)

including all the requirements

And create a php file .. phpinfo.php

```

<?php
echo phpinfo();
?>

```

and drop it into localhost root directory.

then run [http://localhost/phpinfo.php](http://localhost/phpinfo.php)

Do you see php configuration?

---

### Post by yancek on 2016-08-21
> Can anyone tell me my localhost is showing a jumble like this?

It's not a 'jumble', it is the source code of the http page which means you don't have it installed correctly.  Did you ever see the 'Apache2 Ubuntu Default Page' as shown in the second image at the tutorial at the link below.  If you see that, Apache is good and you need to move on to php/perl, mysql.  I'd suggest reading through the tutorial below or going to the second link which is the official Ubuntu documentation page.  Also, the address shown in the browser is to moodle so what is in that directory?  Do you have some kind of index file (html, php0?

[https://www.howtoforge.com/tutorial/install-apache-with-php-and-mysql-on-ubuntu-16-04-lamp/](https://www.howtoforge.com/tutorial/install-apache-with-php-and-mysql-on-ubuntu-16-04-lamp/)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by dodo125025 on 2016-08-21
Thanks guys. I thought Ubuntu was packaged with PHP, but looks like it is not!?

---

