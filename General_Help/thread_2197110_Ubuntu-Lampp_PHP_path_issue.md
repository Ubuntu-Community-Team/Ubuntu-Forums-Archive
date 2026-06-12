---
title: "Ubuntu-Lampp PHP path issue"
date: 2014-01-02
forum: General Help
---

### Post by giannhs905 on 2014-01-02
[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]I use Ubuntu 13.10 and Lampp.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]When I try to run sudo php artisan job-daemon I get: Laravel requires mCrypt PHP extension.
 
But when I run php artisan job-daemon it works just fine.[/FONT][/COLOR]
[/SIZE][COLOR=#333333][FONT=UbuntuRegular][SIZE=3]
php -m gives me the following:
[/SIZE]
[/FONT][/COLOR]
[PHP Modules]
bcmath
bz2
.
.
.
.
mcrypt
.
.
.
xsl
zip
zlib

[Zend Modules]


[SIZE=3][COLOR=#000000][FONT=Arial]which php gives me :[/FONT][/COLOR]
[COLOR=#800000]/opt/[/COLOR]lampp/bin/php
[COLOR=#000000][FONT=Arial]
while sudo which php gives me[/FONT][/COLOR]
[COLOR=#800000]/usr/[/COLOR]bin/php
[COLOR=#000000][FONT=Arial]
I have edited the ~./bashrc as following:[/FONT][/COLOR]
[COLOR=#00008B]export[/COLOR] PATH=$PATH:[COLOR=#800000]/opt/[/COLOR]lampp/bin/php
But still no luck..[/SIZE]

---

### Post by Dave_L on 2014-01-02
What's the output from this:

```
echo $PATH
sudo -i
echo $PATH
exit
```

---

### Post by SeijiSensei on 2014-01-02
The mcrypt module is not installed by default in Ubuntu.  Use "sudo apt-get install php5-mcrypt".  However, you should be aware that there was a packaging error in some recent Ubuntu versions like 13.10 that kept the module from loading when Apache was restarted. If it doesn't appear after installation and a restart, follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=2184310&p=12832240&viewfull=1#post12832240").

You can see what modules are loaded by creating a simple one-line script containing "<?php phpinfo()?>".

---

