---
title: "apache2 not logging"
date: 2007-05-26
forum: General Help
---

### Post by oldtappan on 2007-05-26
Activity on apache2 on Feisty was getting logged and two nights ago, logging stopped.  Restarting apache and even booting my server hasn't helped.  apache2 is working fine, so I guess there must be some misconfiguration WRT logging.

The only config changes are to a file in conf.d:
[B]Alias /site1 /mnt/a

<Directory /mnt/a>
  Options FollowSymLinks
  AllowOverride Limit Options FileInfo
</Directory>[/B]

Any reason why this would break logging?  Site visits were getting logged to /var/log/apache2/access.log  Now it's broken.  I don't see any errors in error.log.

Also, I looked at apache2.conf and I don't see where logging info is being configured.  For example, where is logging dir and file specified?

---

### Post by mbradlcu on 2007-05-27
I'm not sure how it's supposed to be setup but here's (were I believe) apache2 gets it logging directive:
root@matt-x64:~# find /etc -type f -exec grep -iln 'access.log' {} \;
/etc/fail2ban.conf
 
maybe add to your site1 config:
ErrorLog /var/log/apache2/error.log
CustomLog /var/log/apache2/access.log combined

---

