---
title: "help with lamp/owncloud install"
date: 2021-06-06
forum: General Help
---

### Post by worldwidejoe on 2021-06-06
Hello all, not sure of the most accurate forum to put this post in, mods will relocate as they see fit.

Trying to install owncloud on ubuntu 20.04 desktop. 

Apache installed and running.
mysql installed and running.
php version 7.4.3
ufw is disabled.

```
user@comp:~$ sudo systemctl status apache2
[sudo] password for user: 
&#9679; apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor prese>
     Active: active (running) since Sun 2021-06-06 16:20:45 PDT; 1min 11s ago
       Docs: https://httpd.apache.org/docs/2.4/
    Process: 1199 ExecStart=/usr/sbin/apachectl start (code=exited, status=0/SU>
   Main PID: 1506 (apache2)
      Tasks: 55 (limit: 18769)
     Memory: 11.0M
     CGroup: /system.slice/apache2.service
             &#9500;&#9472;1506 /usr/sbin/apache2 -k start
             &#9500;&#9472;1507 /usr/sbin/apache2 -k start
             &#9492;&#9472;1508 /usr/sbin/apache2 -k start

Jun 06 16:20:44 comp systemd[1]: Starting The Apache HTTP Server...
Jun 06 16:20:44 comp apachectl[1267]: AH00558: apache2: Could not reliably >
Jun 06 16:20:45 comp systemd[1]: Started The Apache HTTP Server.

user@comp:~$ sudo systemctl status mysql
&#9679; mariadb.service - MariaDB 10.3.29 database server
     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor prese>
     Active: active (running) since Sun 2021-06-06 16:20:45 PDT; 1min 19s ago
       Docs: man:mysqld(8)
             https://mariadb.com/kb/en/library/systemd/
    Process: 1200 ExecStartPre=/usr/bin/install -m 755 -o mysql -g root -d /var>
    Process: 1227 ExecStartPre=/bin/sh -c systemctl unset-environment _WSREP_ST>
    Process: 1234 ExecStartPre=/bin/sh -c [ ! -e /usr/bin/galera_recovery ] && >
    Process: 1467 ExecStartPost=/bin/sh -c systemctl unset-environment _WSREP_S>
    Process: 1479 ExecStartPost=/etc/mysql/debian-start (code=exited, status=0/>
   Main PID: 1323 (mysqld)
     Status: "Taking your SQL requests now..."
      Tasks: 31 (limit: 18769)
     Memory: 96.3M
     CGroup: /system.slice/mariadb.service
             &#9492;&#9472;1323 /usr/sbin/mysqld

Jun 06 16:20:44 comp systemd[1]: Starting MariaDB 10.3.29 database server...
Jun 06 16:20:44 comp mysqld[1323]: 2021-06-06 16:20:44 0 [Note] /usr/sbin/m>
Jun 06 16:20:45 comp systemd[1]: Started MariaDB 10.3.29 database server.
Jun 06 16:20:45 comp /etc/mysql/debian-start[1486]: Upgrading MySQL tables >
Jun 06 16:20:45 comp /etc/mysql/debian-start[1489]: Looking for 'mysql' as:>
Jun 06 16:20:45 comp /etc/mysql/debian-start[1489]: Looking for 'mysqlcheck>

user@comp:~$ sudo systemctl status php
Unit php.service could not be found.
user@comp:~$ sudo php -v
PHP 7.4.3 (cli) (built: Oct  6 2020 15:47:56) ( NTS )
Copyright (c) The PHP Group
Zend Engine v3.4.0, Copyright (c) Zend Technologies
    with Zend OPcache v7.4.3, Copyright (c), by Zend Technologies
```

I created a databse and a user and granted privleges. I downloaded mysql workbench a gui tool, I can use it to connect to the db. 

Here is what should be the configuration web page to setup owncloud, instead I get this. I have absolutely no idea what the content of this page is unfortunately. The last line reads: "If we've reached this point, something has gone really wrong because // we couldn't even get the logger, so don't rely on ownCloud here." That's why I'm here instead of the owncloud forums. ** the html code tags in this editor made it 2 lines in height, so I just pasted it as/is, it's more legible.

```
* @author Lukas Reschke   * @author Morris Jobke   * @author Philipp Schaffrath   * @author RealRancor   * @author Robin Appelman   * @author Sergio BertolÃ*n   * @author Thomas MÃ¼ller   * @author Vincent Petry   *  * @copyright Copyright (c) 2018, ownCloud GmbH  * @license AGPL-3.0  *  * This code is free software: you can redistribute it and/or modify  * it under the terms of the GNU Affero General Public License, version 3,  * as published by the Free Software Foundation.  *  * This program is distributed in the hope that it will be useful,  * but WITHOUT ANY WARRANTY; without even the implied warranty of  * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the  * GNU Affero General Public License for more details.  *  * You should have received a copy of the GNU Affero General Public License, version 3,  * along with this program.  If not, see   *  */  // Show warning if a PHP version below 7.1.0 is used, this has to happen here // because base.php will already use 7.1 syntax. if (\version_compare(PHP_VERSION, '7.1.0') === -1) {     echo 'This version of ownCloud requires at least PHP 7.1.0
';     echo 'You are currently running PHP ' . PHP_VERSION . '. Please update your PHP version.';     return; }  // Show warning if PHP 7.4 or later is used as ownCloud is not compatible with PHP 7.4 if (\version_compare(PHP_VERSION, '7.4.0alpha1') !== -1) {     echo 'This version of ownCloud is not compatible with PHP 7.4
';     echo 'You are currently running PHP ' . PHP_VERSION . '.';     return; }  // running oC on Windows is unsupported since 8.1, this has to happen here because // is seems that the autoloader on Windows fails later and just throws an exception. if (\stripos(PHP_OS, 'WIN') === 0) {     echo 'ownCloud Server does not support Microsoft Windows.';     return; }  try {     require_once __DIR__ . '/lib/base.php';     OC::handleRequest(); } catch (\OC\ServiceUnavailableException $ex) {     \OC::$server->getLogger()->logException($ex, ['app' => 'index']);      //show the user a detailed error page     OC_Response::setStatus(OC_Response::STATUS_SERVICE_UNAVAILABLE);     OC_Template::printExceptionErrorPage($ex); } catch (\OC\HintException $ex) {     OC_Response::setStatus(OC_Response::STATUS_SERVICE_UNAVAILABLE);     OC_Template::printErrorPage($ex->getMessage(), $ex->getHint()); } catch (\OC\User\LoginException $ex) {     OC_Response::setStatus(OC_Response::STATUS_FORBIDDEN);     OC_Template::printErrorPage($ex->getMessage()); } catch (\OCP\Files\ForbiddenException $ex) {     OC_Response::setStatus(OC_Response::STATUS_FORBIDDEN);     OC_Template::printErrorPage($ex->getMessage()); } catch (\Throwable $ex) {     try {         \OC::$server->getLogger()->logException($ex, ['app' => 'index']);          //show the user a detailed error page         OC_Response::setStatus(OC_Response::STATUS_INTERNAL_SERVER_ERROR);         OC_Template::printExceptionErrorPage($ex);     } catch (\Throwable $ex2) {         // with some env issues, it can happen that the logger couldn't log properly,         // so print out the exception directly         // NOTE: If we've reached this point, something has gone really wrong because         // we couldn't even get the logger, so don't rely on ownCloud here.         \header("{$_SERVER['SERVER_PROTOCOL']} 599 Broken");         \OC::crashLog($ex);         \OC::crashLog($ex2);     } } 
```

Please let me know if anyone can point me in the right direction. Thank you very much.

---

### Post by CharlesA on 2021-06-06
Sounds like you don't have php working correctly.

Can you make the file referenced here ([https://superuser.com/questions/74233/how-to-confirm-php-enabled-on-ubuntu-server](https://superuser.com/questions/74233/how-to-confirm-php-enabled-on-ubuntu-server)) and see if it displays via the browser?

---

### Post by CharlesA on 2021-06-07
Just in case you haven't already seen it, there is an install guide for Ubuntu 20.04 on the owncloud site:
[https://doc.owncloud.com/server/admin_manual/installation/quick_guides/ubuntu_20_04.html](https://doc.owncloud.com/server/admin_manual/installation/quick_guides/ubuntu_20_04.html)

Based on the error in your OP, it sounds like you are missing the php packages for apache.

---

### Post by worldwidejoe on 2021-06-07
Thank you CharlesA for the reply's. 

Good call on the php. I had the wrong version of php installed, I changed from php7.4 to php7.3 and got to the owncloud web interface page. Unfortunately it asks for packages I don't have as you mentioned. Somehow I did not see that owncloud  install guide for Ubuntu 20.04, thank you for the link. I was following 2 other guides that were very different from that. I'll be working on it next. 

Thanks so much!

---

### Post by CharlesA on 2021-06-08
Good luck. I haven't dealt with OwnCloud in a long time. The last time I did, I was running it on Nginx and php5-fpm, so it's been quite a while.

---

### Post by ActionParsnip on 2021-06-08
Remember to mark as solved if all is well ;)

---

