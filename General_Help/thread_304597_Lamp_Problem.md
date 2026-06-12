---
title: "Lamp Problem"
date: 2006-11-22
forum: General Help
---

### Post by Darkstar2525 on 2006-11-22
trying to get php5, apache2, and postgresql 8.1 set up on Ubuntu Edgy Eft

everything installed fine but i keep getting this error when I open [http://localhost/](http://localhost/) in a browser

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

index.php has the following code in it:
[PHP]
<?php 
phpinfo();
?>
[/PHP]

Any help would be great.

---

### Post by Average Joe on 2006-11-22
Weird. Are you sure you have installed php5 for the Apache **2** server? There is also the php5 package for the "old" apache server in the repositories. If you mix those up things might go wrong.

Apart from that, I wouldn't know. You PHP code doesn't seem too complicated. :)

---

### Post by compwiz18 on 2006-11-22
Check the file permissions on index.php.

---

### Post by Darkstar2525 on 2006-11-22
I changed to permissions on the index.php and it worked! Thanks.

---

