---
title: "Apache+PHP-FPM 503 pages and not processing PHP files"
date: 2016-10-05
forum: General Help
---

### Post by bw4linux2 on 2016-10-05
For some reason, PHP scripts are not processed anymore, but they try to download. Just before this, half the time I got 503 service not available pages, the other half the time the pages loaded very slowly. All I did was restart Apache and change log level for PHP-FPM. I'm providing config files, if you need any more information please let me know.

Go to this Gist to see the configuration files: [https://gist.github.com/skinuxgeek/d47994d21e1cc0df54b56218c18f5f7d](https://gist.github.com/skinuxgeek/d47994d21e1cc0df54b56218c18f5f7d)

---

### Post by SeijiSensei on 2016-10-06
Make sure you have the libapache2-mod-php5 (or php7) package installed.

---

