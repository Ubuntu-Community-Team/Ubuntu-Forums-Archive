---
title: "PHP on ubuntu - saying missing modules are installed"
date: 2014-07-17
forum: General Help
---

### Post by Sharkadder on 2014-07-17
Hi there,

I was asked to upgrade my PHP version from 5.3 to 5.5 by somebody and have to revert it back down to 5.3 again due to a website not being compatible with 5.5 functions.  Once i downgraded, some of my modules stopped working; these were:
[I]
opache.so
json.so[/I]

Basically the cron was e-mailing me every 30 minutes complaining that json.so and opache.so were missing.

*Failed loading opcache.so:  opcache.so: cannot open shared object file: No such file or directory PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/json.so' - /usr/lib/php5/20090626/json.so: cannot open shared object file: No such file or directory in Unknown on line 0 Failed loading opcache.so:  opcache.so: cannot open shared object file: No such file or directory PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626/json.so' - /usr/lib/php5/20090626/json.so: cannot open shared object file: No such file or directory in Unknown on line 0*

I have checked and opache is now on my untuntu server after installing it but the server would not find it; to get around this i put the following command into my php.ini file:
zend_extension=/usr/lib/php5/20090626/opcache.so

The problem i have now got is that every time a cron tab runs i get the following message in the e-mail:

Aborted
<end>

The subject line of the e-mail also shows this:[I]
Cron <****@*****>   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete[/I]

Has anybody got any idea why this could be happening?  I have also not got json.so back on either and so that module is still missing.  Would it be best to just reinstall php and then everything would be back to normal?  When i have done the command below it just says json is already installed but it isn't:
sudo apt-get install php5-json

> sudo find / -name 'json.so' <---this shows nothing on the server

There is a cron job set up on my webmin to go off every 9 and 38 minutes (which does explain the e-mails but i never used to get them before the upgrade/downgrade).  Cron job is:

[ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete

You will notice the cron is the same as the subject line.  Hope somebody can point me in the right direction as to what is going in as never noticed this before.

Many thanks :-),

Mark

---

