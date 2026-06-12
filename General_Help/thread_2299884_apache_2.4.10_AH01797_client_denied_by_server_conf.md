---
title: "apache 2.4.10 AH01797 client denied by server configuration"
date: 2015-10-22
forum: General Help
---

### Post by artur18 on 2015-10-22
[FONT=Helvetica Neue]sites began to give 403 error. Logs apache:
```
[/FONT][Sun Oct 18 23:07:23.956826 2015] [access_compat:error] [pid 7950] [client 127.0.0.1:46765] AH01797: client denied by server configuration: /var/www/sitename.local/index.php[FONT=Helvetica Neue]
```
[/FONT][FONT=Helvetica Neue]in Apache config like all the rules[/FONT][FONT=Helvetica Neue]```
[/FONT][FONT=Consolas]<Directory /var/www/>[/FONT]
  Options Indexes FollowSymLinks  AllowOverride All  Require all granted [FONT=Consolas]</Directory>[/FONT][FONT=Helvetica Neue]
```
[/FONT][FONT=Helvetica Neue]All Rights bear. Previously everything worked. How to fix?
[/FONT]

localhost/phpmyadmin/ - It works fine

phpmyadmin config - [https://yadi.sk/i/qpUvvZSWjtGbV](https://yadi.sk/i/qpUvvZSWjtGbV)
apache config - [https://yadi.sk/i/Tw5Rj41MjtEZF](https://yadi.sk/i/Tw5Rj41MjtEZF)

---

