---
title: "Apache 2.4 on Ubuntu 14 refuses to load an index.php even though PHP is working."
date: 2015-11-19
forum: General Help
---

### Post by routermods on 2015-11-19
[SIZE=2]My apache won't load a index.php one one of my vhosts not even if I type in example.com/index.php. I have two and one works fine.

The second vhost is my issue.

Any help would be appreciated, idk what changed between apache and php version but I am missing something. Any help would be appreciated.

I am posting both vhosts below exact copies.

First one:[/SIZE]
<VirtualHost *:80>
ServerAdmin webmaster@localhost
ServerName domain1.com
ServerAlias www.domain1.com
DocumentRoot /var/www/domain1.com/htdocs
DirectoryIndex index.php
<Directory />
AllowOverride All
</Directory>
<Directory /var/www/domain1.com/htdocs>
Options Indexes FollowSymLinks MultiViews
AllowOverride all
Require all granted
</Directory>
ErrorLog /var/log/apache2/domain1.com-error.log
LogLevel error
CustomLog /var/log/apache2/domain1.com-access.log combined

<IfModule security2_module>
SecRuleEngine Off
</IfModule>

phpMyAdmin default Apache configuration
Alias /ms /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
Options FollowSymLinks
DirectoryIndex index.php

<IfModule mod_php5.c>
AddType application/x-httpd-php .php

phpflag magicquotesgpc Off
phpflag trackvars On
phpflag registerglobals Off
phpadminflag allowurlfopen Off
phpvalue includepath .
phpadminvalue uploadtmpdir /var/lib/phpmyadmin/tmp
phpadminvalue openbasedir /usr/share/phpmyadmin/:/etc/phpmyadmin/:/var/lib/phpmyadmin/:/usr/share/php/php-gettext/:/usr/share/javascript/
</IfModule>

</Directory>

Authorize for setup
<Directory /usr/share/phpmyadmin/setup>
<IfModule mod_authn_file.c>
AuthType Basic
AuthName "phpMyAdmin Setup"
AuthUserFile /etc/phpmyadmin/htpasswd.setup
</IfModule>
Require valid-user
</Directory>

Disallow web access to directories that don't need it
<Directory /usr/share/phpmyadmin/libraries>
Order Deny,Allow
Deny from All
</Directory>
<Directory /usr/share/phpmyadmin/setup/lib>
Order Deny,Allow
Deny from All
</Directory>

</VirtualHost>

[SIZE=2]Second one:[/SIZE]

<VirtualHost *:80>
ServerAdmin webmaster@localhost
ServerName domain2.com
ServerAlias www.domain2.com
DocumentRoot /var/www/domain2.com
<IfModule dir_module>
DirectoryIndex index.html
DirectoryIndex index.php
</IfModule>
<Directory />
AllowOverride All
</Directory>
<Directory /var/www/domain2.com>
Options Indexes FollowSymLinks MultiViews
DirectoryIndex index.php
AllowOverride all
Require all granted
</Directory>
ErrorLog /var/log/apache2/domain2.com-error.log
LogLevel debug
CustomLog /var/log/apache2/domain2.com-access.log combined
</VirtualHost>

---

