---
title: "Upgrading PHP and MySQL"
date: 2013-10-02
forum: General Help
---

### Post by John_Wiget on 2013-10-02
Dear all,

I have install Ubuntu 13.04. How can i update the php to latest version 5.4.20 and MySQL 5.5.34?

Regards,
John

---

### Post by SeijiSensei on 2013-10-03
If you want to pick specific versions, you'll probably have to compile them.  If you want to stick to .debs, then you'll have to adjust your requirements.

Right now the current update for PHP on 13.04 in [raring-updates]("http://packages.ubuntu.com/raring-updates/php5") is 5.4.9.  You could try installing the forthcoming "[saucy]("http://packages.ubuntu.com/saucy/php5")" .deb which has 5.5.3, but there may be a lot of dependencies that you would need as well.

Is there something specific you need in PHP 5.4.20 that isn't in 5.4.9?  Remember that security flaws are fixed as soon as they are discovered, so I doubt 5.4.9 is any less secure than 5.4.20.

The saucy version of [MySQL]("http://packages.ubuntu.com/saucy/mysql-server") is 5.5.32, just a tad behind the one you seek.

You might be better off waiting until saucy is released on October 17th and upgrading the whole system then.

---

