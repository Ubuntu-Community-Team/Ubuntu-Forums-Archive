---
title: "Wordpress Plugin Install Fail"
date: 2014-02-16
forum: General Help
---

### Post by aimless2 on 2014-02-16
I'm only working locally right now.  What permissions am I missing and on what directories?

Thanks!

[[IMG]http://i.imgur.com/sSNNzQO.png[/IMG]]("http://imgur.com/sSNNzQO")

---

### Post by Habitual on 2014-02-17
plugins directory needs  to be writable by the apache owner or group.
On Ubuntu 12.04.4 LTS it is drwxr-xr-x 20 www-data www-data 4096 Feb 12 09:05 /var/www/site/wp-content/plugins

open a terminal and as root, issue this:```

find /var/www -name plugins -type d | grep wp-content

```
then let's see perms using:
```
ls -ld <that result>
```

Post that here please.

---

