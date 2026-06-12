---
title: "PHP Apache2  problem"
date: 2007-06-05
forum: General Help
---

### Post by Luis McDOugall on 2007-06-05
HI!

I am having a problem with php5 and Apache2. I cannot make it work.
I have installed Apache2 which seems to be working ok, but php is not.
I cannot find the module.
but when I apt-get install php5 or libapache2-mod-php5 it tell me that is already installed.
then I do a2wnmod php5 and is complains "This module does not exist.

HELP!

ubuntu 7.04.

-L:(:confused::mad:

---

### Post by eggdeng on 2007-06-06
a2wnmod?? Why dont you just create a test.php file, stick ```
<?php phpinfo(); ?>
``` in it and save it to /var/www. Then open it from your browser at localhost/test.php. Makes the yop chagui look easy, doesn't he.

---

### Post by Luis McDOugall on 2007-06-07
I am following instructions on installing php,
but <?  phpinfo(); ?>
does not work
As expected.

---

### Post by gerscht on 2007-06-07
Does apache start e.g are you getting the text-output from phpinfo()?
which modules are loaded via your httpd.conf?

apt-get install libapache2-mod-php5 should have added a line to httpd.conf

---

