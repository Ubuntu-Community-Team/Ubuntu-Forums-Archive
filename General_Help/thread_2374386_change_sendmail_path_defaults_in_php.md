---
title: "change sendmail_path defaults in php"
date: 2017-10-15
forum: General Help
---

### Post by mauro_ita on 2017-10-15
Hi,

I'm struggeling setting up php to send email

I tried sendmailconfig with no good results

Than I tried msmtp, installed, configured changed php.ini and saved, restart apache2 but still nothing good

If I run phpinfo() on a browser it still shows sendmail_path is the default

[HTML]
sendmail_from	no value	no value
sendmail_path	/usr/sbin/sendmail -t -i 	/usr/sbin/sendmail -t -i [/HTML]

So, why php doesn't get php.ini changes?

Accordingly to php.net manual
[http://php.net/manual/en/mail.configuration.php#ini.sendmail-path](http://php.net/manual/en/mail.configuration.php#ini.sendmail-path)

[http://php.net/manual/en/configuration.changes.modes.php](http://php.net/manual/en/configuration.changes.modes.php)

I'm stacked :(

Thanks for helps

---

