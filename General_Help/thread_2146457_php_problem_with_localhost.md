---
title: "php problem with localhost"
date: 2013-05-18
forum: General Help
---

### Post by bangba on 2013-05-18
I set up a virtualhost with an index.html (It Works test page) and it works.  If I take it out and put in index.php I get a blank scrren on localhost. Info.php works on localhost.  What is not connecting in my php & apache?

---

### Post by Geoff918 on 2013-05-18
Well, you may have a configuration problem. Are the server settings set to parse .PHP files through the interpreter? It sounds like the settings may work if you simply change the end of the file to a .HTML file.

---

### Post by bangba on 2013-05-18
If you are talking about adding .html in the php5.conf, yes i have tried that and it doesnt work

---

### Post by bangba on 2013-05-19
I changed my path on my include files and now the page shows the html  but it does not include the include files. The error/warning I get is below

[Sun May 19 07:31:35 2013] [error] [client 127.0.0.1] PHP Warning:  include(): Failed opening '/chaircane/include/includes_bottom.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/chaircane/index.php on line 25

do i need to change my path to whaat it says above verse what I currently have
<?php

include ("/chaircane/include/includes_bottom.php");

?>

---

### Post by pqwoerituytrueiwoq on 2013-05-19
that error means that your requested file [FONT=courier new]/chaircane/include/includes_bottom.php[/FONT] does not exist
i think it should say [FONT=courier new]/var/www/chaircane/include/includes_bottom.php[/FONT] in your script
or you can run this and make that incorrect path a valid path
[FONT=Courier New]sudo ln -s /var/www/chaircane /chaircane[/FONT]

if you enable display errors in your [FONT=Courier New]/etc/php5/apache2/php.ini[/FONT] file (line 480) it will give you error messages on the page instead of giving you blank pages like that

---

