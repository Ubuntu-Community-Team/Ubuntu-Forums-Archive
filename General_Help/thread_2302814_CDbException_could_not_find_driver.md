---
title: "CDbException: could not find driver"
date: 2015-11-13
forum: General Help
---

### Post by Cody_Robinson on 2015-11-13
First of all, this happened out of nowhere. I don't think the server being forced to shutdown helped, but it was working and nobody touched it, I swear.

1) The application uses yii and here is the application.log

```

2015/11/13 14:17:04 [error] [exception.CDbException] [User 1, XXX.XXX.XXX.XXX] could not find driver
2015/11/13 14:17:04 [error] [exception.CDbException] [User 1, XXX.XXX.XXX.XXX] exception 'CDbException' with message 'CDbConnection failed to open the DB connection.' in /path/to/directory/yii/db/CDbConnection.php:405
Stack trace:
#0 /path/to/directory/yii/db/CDbConnection.php(347): CDbConnection->open()
#1 /path/to/directory/yii/base/CComponent.php(152): CDbConnection->setActive(true)
#2 /path/to/directory/models/CommandCache.php(27): CComponent->__set('active', true)
#3 /path/to/directory/models/CommandCache.php(76): CommandCache::getDbConnection()
#4 /path/to/directory/components/McConnection.php(42): CommandCache::get('1', 'daemon down', '', 1)
#5 /path/to/directory/components/McBridge.php(156): McConnection->command('updatejar list ...', Array)
#6 /path/to/directory/controllers/ServerController.php(60): McBridge->cmd('1', 'updatejar list ...')
#7 /path/to/directory/controllers/ServerController.php(229): ServerController->listJars('245')
#8 [internal function]: ServerController->actionView('245')
#9 /path/to/directory/yii/web/actions/CAction.php(109): ReflectionMethod->invokeArgs(Object(ServerController), Array)
#10 /path/to/directory/yii/web/actions/CInlineAction.php(47): CAction->runWithParamsInternal(Object(ServerController), Object(ReflectionMethod), Array)
#11 /path/to/directory/yii/web/CController.php(308): CInlineAction->runWithParams(Array)
#12 /path/to/directory/yii/web/filters/CFilterChain.php(133): CController->runAction(Object(CInlineAction))
#13 /path/to/directory/yii/web/filters/CFilter.php(40): CFilterChain->run()
#14 /path/to/directory/yii/web/CController.php(1145): CFilter->filter(Object(CFilterChain))
#15 /path/to/directory/yii/web/filters/CInlineFilter.php(58): CController->filterAccessControl(Object(CFilterChain))
#16 /path/to/directory/yii/web/filters/CFilterChain.php(130): CInlineFilter->filter(Object(CFilterChain))
#17 /path/to/directory/yii/web/CController.php(291): CFilterChain->run()
#18 /path/to/directory/yii/web/CController.php(265): CController->runActionWithFilters(Object(CInlineAction), Array)
#19 /path/to/directory/yii/web/CWebApplication.php(282): CController->run('view')
#20 /path/to/directory/yii/web/CWebApplication.php(141): CWebApplication->runController('server/view')
#21 /path/to/directory/yii/base/CApplication.php(184): CWebApplication->processRequest()
#22 /var/www/sites/multicraft/index.php(23): CApplication->run()
#23 {main}
REQUEST_URI=/myPage.php
HTTP_REFERER=http://myurl.com/
---

```

It says no driver found, but I already have php5-mysql installed:

```

root@myserver:/# apt-get install php5-mysql
Reading package lists... Done
Building dependency tree
Reading state information... Done
php5-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

Also tried testing the config:

```

root@myserver:/# php5-fpm -t
[13-Nov-2015 14:33:01] NOTICE: configuration file /etc/php5/fpm/php-fpm.conf test is successful

```

Also did php5-fpm -i and cut this bit out

```

mysqli


MysqlI Support => enabled
Client API library version => 5.5.46
Active Persistent Links => 0
Inactive Persistent Links => 0
Active Links => 0
Client API header version => 5.5.46
MYSQLI_SOCKET => /var/run/mysqld/mysqld.sock


Directive => Local Value => Master Value
mysqli.allow_local_infile => On => On
mysqli.allow_persistent => On => On
mysqli.default_host => no value => no value
mysqli.default_port => 3306 => 3306
mysqli.default_pw => no value => no value
mysqli.default_socket => /var/run/mysqld/mysqld.sock => /var/run/mysqld/mysqld.sock
mysqli.default_user => no value => no value
mysqli.max_links => Unlimited => Unlimited
mysqli.max_persistent => Unlimited => Unlimited
mysqli.reconnect => Off => Off


PDO


PDO support => enabled
PDO drivers => dblib, mysql


pdo_dblib


PDO Driver for FreeTDS/Sybase DB-lib => enabled
Flavour => freetds


pdo_mysql


PDO Driver for MySQL => enabled
Client API version => 5.5.46


Directive => Local Value => Master Value
pdo_mysql.default_socket => /var/run/mysqld/mysqld.sock => /var/run/mysqld/mysqld.sock

```

Other info, the MySQL server is able to be connected to (I made a PHP script).

---

### Post by cariboo on 2015-11-13
Did you run fsck after the forced shutdown?

---

### Post by Cody_Robinson on 2015-11-13
> **cariboo said:**
> Did you run fsck after the forced shutdown?

I just ran it, still the same error.

---

