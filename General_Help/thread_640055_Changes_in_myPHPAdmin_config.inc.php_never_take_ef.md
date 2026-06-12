---
title: "Changes in myPHPAdmin config.inc.php never take effct..."
date: 2007-12-13
forum: General Help
---

### Post by worlhin on 2007-12-13
below is part of my config.inc.php;
$cfg['Servers'][$i]['host'] = 'localhost';
$cfg['Servers'][$i]['connect_type'] = 'tcp';
$cfg['Servers'][$i]['extension'] = 'mysql';
$cfg['Servers'][$i]['compress'] = FALSE;
$cfg['Servers'][$i]['auth_type'] = 'http';
$cfg['Servers'][$i]['user'] = 'root';
$cfg['Servers'][$i]['password'] = '';

but when i restart my phpMyAdmin by restarting wampserver2, it still show "#1045 - Access denied for user 'root'@'localhost' (using password: NO)" it seems the changes doesn't reflect on myPhpAdmin... i even restarted my computer but still same result... anyone can tell me what i should do?

Additional Details

It didn't prompt me for password... by right when i set the auth_type to http, it should prompt me for password...
i tried to remove root from user but still the same... the problem is whatever i change in config.inc.php, it seems never reflect on myPhpAdmin..., i tried to change auth_type to config and provide the correct password, but still same result too...
i able to login at mysql console,but not myPhpAdmin...

---

